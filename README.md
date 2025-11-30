# para-3
import datetime
import random

def greet_user(name):
    print(f"Привіт, {name}! Радий тебе бачити 😊")

def answer_request(request):
    if request.lower() == "час":
        now = datetime.datetime.now()
        return f"Зараз {now.strftime('%H:%M:%S')}."
    elif request.lower() == "дата":
        today = datetime.date.today()
        return f"Сьогодні {today.strftime('%d.%m.%Y')}."
    elif request.lower() == "жарт":
        jokes = [
            "Python настільки дружній, що навіть змії ним користуються.",
            "Чому програмісти люблять темну тему? Бо світло приваблює баги!",
            "Код без помилок — це як єдиноріг. Всі чули, але ніхто не бачив."
        ]
        return random.choice(jokes)
    else:
        return "Вибач, я ще не знаю відповіді на цей запит."

# --- Основна програма ---
user_name = input("Введи своє ім'я: ")
greet_user(user_name)

print("Можеш задати запит: 'час', 'дата', 'жарт'")
for i in range(10):
    req = input("Твій запит: ")
    print(answer_request(req))
print("Заїбав запитувати треба було вчитися!!!!!!!!! ")




import datetime

data_1 = datetime.date(2025, 11,30)
time_1 = datetime.time(21,8,48)
print(f"date={data_1}, type data = {type(data_1)}")
print(f"time={time_1}, type time={type(time_1)}")





import datetime

date_time = datetime.datetime(2025,11,30, hour=18,minute=3,microsecond=100)
print(f"method date() - " f"{date_time.date()}\n type of its result - {type(date_time.date())}")




#para 3 part 2
import datetime

data_time = datetime.datetime(2025, 11, 30, hour=17, minute=55, second=12, microsecond=543 )
print(data_time)




import os
path = os.path.normpath("new_dir")
os.rmdir(path)

file = open("file.txt", "w")
file.write("Hello world!")
file.close()
file = open("file.txt", "a")
file.write("Hello user!")
file.close()
file = open("file.txt", "r")
print(file.read())
file.close()







import os

dir_1 = "Windows"
dir_2 = "Web"
path = os.path.join(dir_1, dir_2)
print(path)





import os

path = os.path.normpath("C:/Windows/Web")

for path, dirnames,filenames in os.walk(path):
    print(f"path - {path}")
    print(f"dirname - {dirnames}")
    print(f"filename - {filenames}")









    import datetime
    import os
def collector(path, res_path):
    res_path = os.path.normpath(res_path)
    path = os.path.normpath(path)
    for dirpath, dirnames, filenames in os.walk(path):
        for file in filenames:
            file_time = os.path.getmtime(f"{dirpath}\\{file}")
            datetime_file = datetime.datetime.fromtimestamp(file_time)
            file_date = datetime_file.strftime("%d.%m.%Y")
            if os.path.isdir(f"{res_path}\\{file_date}"):
                os.replace(f"{dirpath}\\{file}", f"{res_path}\\{file_date}\\{file}")
            else:
                os.mkdir(f"{res_path}\\{file_date}\\")
                os.replace(f"{dirpath}\\{file}",f"{res_path}\\{file_date}\\{file}")

path = "D:/Web"
res_path = "D:/agent_data"
collector(path, res_path)











import os
def file_collector(path):
    path = os.path.normpath(path)
    result = {"dirs":[], "files": []}
    for path, dirnames, filenames in os.walk(path):
        for dir in dirnames:
            result["dirs"].append(dir)
        for file in filenames:
            result["files"].append(file)
    with open("skiper.txt","w") as file:
        file.write("\n{:-<50}\n".format("Directories"))
        for dir in result["dirs"]:
            file.write(f"\t{dir}\n")
        file.write("\n{:-<50}".format("Files"))
        for files in result["files"]:
            file.write(f"\t{files}\n")

path = ''
file_collector(path)
