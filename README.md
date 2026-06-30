# pascal
| **Студентка** | Яснова Ксения Сергеевна |                       

---

##  Цель работы

Познакомиться с Docker на практике: создать контейнер для программы на Pascal 🐳

---

## 📁 Структура проекта
pascal-app/
├── Dockerfile
└── hello.pas

## 📄 Содержимое файлов

### 🐋 Файл `Dockerfile`

```dockerfile
# Используем официальный образ с Free Pascal на Ubuntu
FROM primeimages/freepascal:3.2.2

# Создаём рабочую директорию внутри контейнера
WORKDIR /app

# Копируем код из текущей папки в контейнер
COPY hello.pas .

# Компилиция программы компилятором fpc
RUN fpc hello.pas

# Команда для запуска при создании контейнера
CMD ["./hello"]
```
💬 Что здесь происходит?
```
FROM	берём готовый образ с Free Pascal
WORKDIR	переходим в папку /app внутри контейнера
COPY	кладём наш hello.pas внутрь
RUN	компилируем программу
CMD	запускаем её при старте контейнера
```
📝 Файл hello.pas
```
program Hello;
begin
  Writeln('Hello from Pascal in Docker! 🐳');
end.
```

💬 Пояснение:
```
program Hello;	программа называется "Hello"
begin	начинается основная часть
Writeln(...)	выводим сообщение в консоль
end.	программа завершена ✅
```
🚀 Сборка и запуск
### 1️⃣ Собираем образ
В терминале, находясь в папке pascal-app, выполняем:
docker build -t pascal .
<img width="1149" height="393" alt="pascal1" src="https://github.com/user-attachments/assets/9fee4bfa-3f7a-4ad6-a941-9cb69feaa7f7" />

### 2️⃣ Запускаем контейнер
docker run --rm pascal
## 🧹 Флаг --rm автоматически удаляет контейнер после завершения
# 🌟 Результат
 <img width="640" height="37" alt="pascal2" src="https://github.com/user-attachments/assets/8ff53199-e985-4470-bd66-3ea594fe083f" />


