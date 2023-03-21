from random import randrange

#Проверка ГРАНИЧНЫХ ЗНАЧЕНИЙ
def border(left,right):
    
    if left.isdigit()==False or right.isdigit()==False:
        print("Введите именно число")
        
        return False
        
    
    if left==right or int(left)>int(right):
        print("Введите два разных числа, где первое меньше второго")
        
        return False
        
    
    if left.isdigit() and right.isdigit() and int(left)<int(right):
        
        return True
    
        
#Сравнение
def compare(user_num):
    if user_num == quest_num:
        return 0
    if user_num > quest_num:
        return 1
    else:
        return -1
    

#Проверка числа введённого пользователем
def is_valid_member(user_num):
    if not user_num.isdigit():
        print(f"Введите пожалуйста число")
        return False
    if user_num.isdigit():
        return True

    
#Ввод пользователя
def user_input(left,right):
    
    user_num=input()
    print(user_num)
    while not is_valid_member(user_num) or int(left)>int(user_num) or int(right)<int(user_num):
        print(f"А может быть введем целое число от {left} до {right}?")
        user_num=input()
    else:
        user_num = int(user_num)
    return user_num


print("Добро пожаловать в числовую угадайку")
while True:
    left=input("Задайте левую границу диапазона")
    right=input("Задайте правую границу диапазона")
    while not border(left,right):
        print("Ну же, введите числа из диапазона")
        left=input("Введите левую границу")
        right=input("Введите правую границу")
    left, right=int(left), int(right)
    quest_num = randrange(left,right)
    print("Мной создано случайное число")
    try_counter=0
    flag=False
    user_answer=user_input(left,right)
    
    while flag==False:
        if compare(user_answer)==0:
            print("Вы угадали, ура!")
            print(f"Количество сделанных попыток {try_counter}")
            flag==True
            break
        
        if compare(user_answer)==1:
            print("Попробуйте ввести число поменьше")
            try_counter+=1
            user_answer=user_input(left,right)
        if compare(user_answer)==-1:
            print("Попробуйте ввести число побольше")
            try_counter+=1
            user_answer=user_input(left,right)

    is_more = input("Сыграем ещё? Да/нет")
    if is_more.lower() != "да":
        print("Спасибо что поиграли, до встречи")
        break
