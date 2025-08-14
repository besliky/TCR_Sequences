Как установить WSL (Linux) на **Windows 10**.

1. Самый быстрый путь (Windows 10 ≥2004). Открой PowerShell **от имени администратора** и выполните:

```powershell
wsl --install
# или выбрать дистрибутив, например:
wsl --install -d Ubuntu-22.04
```

2. Нажмите Win+R и вбейте cmd и нажмите Enter.

3. Вход в WSL (выполняется в появившимся терминале).
```
wsl
```

4. Установка Git.
```
sudo apt update && sudo apt install git
```

5. Клонирование репозитория.
```
git clone https://github.com/besliky/TCR_Sequences.git
```

6. Переход в репозиторий.
```
cd TCR_Sequences/
```