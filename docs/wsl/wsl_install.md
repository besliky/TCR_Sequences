Как установить WSL (Linux) на **Windows 10**.

1. Самый быстрый путь (Windows 10 ≥2004). Открой PowerShell **от имени администратора** и выполните:

```powershell
wsl --install
# или выбрать дистрибутив, например:
wsl --install -d Ubuntu-22.04
```
2. Вход в WSL.
```
wsl
```

3. Установка Git.
```
sudo apt update && sudo apt install git
```

4. Клонирование репозитория.
```
git clone https://github.com/besliky/TCR_Sequences.git
```

5. Переход в репозиторий.
```
cd TCR_Sequences/
```