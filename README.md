# TCR Sequences Analysis

Анализ данных секвенирования T-клеточных рецепторов (TCR) с использованием SeekSoulTools v1.3.0.

## 📁 Структура проекта

```
TCR_Sequences/
├── data/                          # Исходные данные секвенирования
│   ├── 20023_3_library_TCR_L01_R1.fq.gz
│   └── 20023_3_library_TCR_L01_R2.fq.gz
├── results/                       # Результаты анализа
│   ├── tcr_analysis/             # Результаты TCR анализа
│   └── *.html                    # Отчеты FastQC
├── tools/                        # Инструменты
│   └── seeksoultools.1.3.0/      # SeekSoulTools
└── docs/                         # Документация
    └── seeksoultools/
        └── seeksoultools_install.md
```

## 🚀 Быстрый старт

### 1. Анализ качества данных
```bash
# Установка FastQC
sudo apt update && sudo apt install -y fastqc

# Создание папки для результатов
mkdir -p results

# Анализ качества
fastqc data/*.fq.gz -o results/ -t 4
```

### 2. TCR анализ
```bash
# Переход в папку инструмента
cd tools/seeksoultools.1.3.0

# Сделать скрипт исполняемым
chmod +x seeksoultools

# Запуск анализа TCR
./seeksoultools vdj run \
    --fq1 /path/to/your/R1.fq.gz \
    --fq2 /path/to/your/R2.fq.gz \
    --samplename YOUR_SAMPLE_NAME \
    --outdir /path/to/results/tcr_analysis \
    --chain TR \
    --core 8 \
    --organism human
```

## 📋 Шаблоны команд

### Для ваших данных:
```bash
./seeksoultools vdj run \
    --fq1 ../data/20023_3_library_TCR_L01_R1.fq.gz \
    --fq2 ../data/20023_3_library_TCR_L01_R2.fq.gz \
    --samplename TCR_20023_3_library \
    --outdir ../results/tcr_analysis \
    --chain TR \
    --core 8 \
    --organism human
```

### Для других образцов:
```bash
./seeksoultools vdj run \
    --fq1 /path/to/sample_R1.fq.gz \
    --fq2 /path/to/sample_R2.fq.gz \
    --samplename SAMPLE_NAME \
    --outdir /path/to/results/tcr_analysis \
    --chain TR \
    --core 8 \
    --organism human
```

## 📊 Результаты анализа

### Основные файлы:
- `results/tcr_analysis/SAMPLE_NAME/Outs/SAMPLE_NAME_report.html` - Интерактивный HTML отчет
- `results/tcr_analysis/SAMPLE_NAME/Outs/SAMPLE_NAME_clonotypes.tsv` - Таблица клонотипов
- `results/tcr_analysis/SAMPLE_NAME/Outs/metrics_summary.csv` - Сводная статистика
- `results/tcr_analysis/SAMPLE_NAME/Outs/SAMPLE_NAME_airr_rearrangement.tsv` - AIRR формат

### Ключевые метрики:
- **Количество клеток**: 92
- **Клетки с TCR**: 74 (80.43%)
- **Уникальных клонотипов**: 44
- **Качество данных**: Q30 > 94%

## 📚 Документация

### Установка и настройка:
- [Руководство по установке SeekSoulTools](docs/seeksoultools/seeksoultools_install.md)

### Официальная документация:
- [SeekSoulTools Tutorial](http://seeksoul.seekgene.com/en/v1.3.0/2.tutorial.html)
- [SeekSoulTools Documentation](http://seeksoul.seekgene.com/en/v1.3.0/)

### Интерактивная помощь:
- [Google NotebookLM для SeekSoulTools 1.3.0](https://notebooklm.google.com/)
- [Настроенный ноутбук для SeekSoulTools](https://clck.ru/3NerJ8)

## 🔧 Параметры анализа

| Параметр | Описание | Пример |
|----------|----------|---------|
| `--fq1` | R1 fastq файл | `/path/to/R1.fq.gz` |
| `--fq2` | R2 fastq файл | `/path/to/R2.fq.gz` |
| `--samplename` | Имя образца | `TCR_sample_001` |
| `--outdir` | Папка результатов | `/path/to/results` |
| `--chain` | Тип цепи | `TR` (TCR) или `BCR` |
| `--core` | Количество ядер | `8` |
| `--organism` | Организм | `human` |


## 🆘 Устранение проблем

### Ошибка "Path does not exist":
```bash
# Используйте абсолютные пути
pwd  # Узнайте текущий путь
ls /path/to/your/files  # Проверьте существование файлов
```

### Ошибка "conda-unpack":
```bash
# Это нормальное предупреждение, можно игнорировать
# SeekSoulTools работает корректно
```

### Медленный анализ:
```bash
# Уменьшите количество ядер
--core 4  # Вместо 8
```
