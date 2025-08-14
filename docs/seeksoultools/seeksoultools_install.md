### Краткое руководство по установке SeekSoulTools через WSL

Вот пошаговая инструкция, как войти в WSL, скачать и подготовить к работе `seeksoultools`.

**1. Войдите в WSL**

*   Откройте меню "Пуск" в Windows.
*   Начните вводить `wsl` или название вашего дистрибутива (например, `Ubuntu`).
*   Нажмите на иконку приложения, чтобы открыть терминал Linux.

**2. Скачайте архив**

*   В открывшемся терминале WSL выполните следующую команду, чтобы скачать файл с помощью `wget`. Опция `-O` сразу переименовывает скачиваемый файл в `seeksoultools.1.3.0.tar.gz`.

```bash
wget -c -O seeksoultools.1.3.0.tar.gz "https://seekgene-public.oss-cn-beijing.aliyuncs.com/software/seeksoultools/seeksoultools.1.3.0.tar.gz"
```

**3. Распакуйте архив**

*   После завершения загрузки используйте команду `tar` для извлечения файлов из архива:

```bash
tar -zxvf seeksoultools.1.3.0.tar.gz
```

**4. Настройка и использование**

*   Перейдите в созданную папку:

```bash
cd seeksoultools.1.3.0
```

*   Сделайте основной скрипт исполняемым:

```bash
chmod +x seeksoultools
```

*   Теперь вы можете использовать инструмент, вызывая его по имени:

```bash
./seeksoultools --version
```

**5. Примеры использования**

SeekSoulTools поддерживает несколько типов анализа:

**RNA-seq анализ:**
```bash
./seeksoultools rna run \
    --fq1 /path/to/your/R1.fq.gz \
    --fq2 /path/to/your/R2.fq.gz \
    --chemistry DD5V1 \
    --samplename your_sample \
    --outdir output_directory \
    --genomeDir /path/to/genome/index \
    --gtf /path/to/annotation.gtf \
    --include-introns \
    --core 4
```

**TCR/BCR анализ:**
```bash
./seeksoultools vdj run \
    --fq1 /path/to/your/R1.fq.gz \
    --fq2 /path/to/your/R2.fq.gz \
    --samplename your_sample \
    --outdir output_directory \
    --chain TR \
    --core 8 \
    --organism human
```

**Мульти-омикс анализ (RNA + TCR):**
```bash
./seeksoultools multivdj run \
    --rnafq1 /path/to/rna/R1.fq.gz \
    --rnafq2 /path/to/rna/R2.fq.gz \
    --tcrfq1 /path/to/tcr/R1.fq.gz \
    --tcrfq2 /path/to/tcr/R2.fq.gz \
    --samplename your_sample \
    --organism human \
    --core 8 \
    --genomeDir /path/to/genome/index \
    --gtf /path/to/annotation.gtf \
    --include-introns \
    --outdir output_directory
```

**6. Демонстрация**

*   Для запуска демо-примеров используйте:

```bash
./demo.sh
```

*   Это запустит все типы анализа на демо-данных.

**7. Дополнительная информация**

*   Туториал по SeekSoulTools 1.3.0: http://seeksoul.seekgene.com/en/v1.3.0/2.tutorial.html
*   Официальная документация: http://seeksoul.seekgene.com/en/v1.3.0/