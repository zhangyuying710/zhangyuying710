# Домашнее задание №1
__Подготовлено__:
**ФИО**:
Чжан Юйин
**ИСУ**:
426409
test 1
def fix_variable_name(variable_name):
    # 1. Замена символов '-' на '_'
    variable_name = variable_name.replace('-', '_')
    
    # 2. Преобразование CamelCase в snake_case
    new_name = []
    word = ''
    
    for char in variable_name:
        if char.isupper():
            if word:  # если слово уже есть, добавляем его к списку
                new_name.append(word.lower())
                word = ''
            word += char
        elif char.islower() or char.isdigit():
            word += char
        else:
            if word:  # добавляем предыдущее слово, если есть
                new_name.append(word.lower())
                word = ''
    
    if word:  # добавляем последнее слово
        new_name.append(word.lower())
    
    variable_name = '_'.join(new_name)
    
    # 3. Заменяем пробелы на '_' и удаляем лишние '_'
    variable_name = variable_name.strip().replace(' ', '_')
    
    while '__' in variable_name:
        variable_name = variable_name.replace('__', '_')
    
    # 4. Удаляем начальные цифры
    while variable_name and variable_name[0].isdigit():
        variable_name = variable_name[1:]
    
    # 5. Проверка на допустимые символы
    if not all(c.isalnum() or c == '_' for c in variable_name):
        return "Введено некорректное имя переменной"
    
    return variable_name if variable_name else "Введено некорректное имя переменной"
test2
def display_products(products):
    print("| ID  | ProductName | Цена |")
    print("|-----|-------------|------|")
    for product in products:
        print(f"| {product['id']:<3} | {product['name']:<11} | {product['price']:>4} |")

def main():
    products = [
        {"id": "001", "name": "Батончик", "price": 70},
        {"id": "002", "name": "Вода", "price": 45},
        {"id": "003", "name": "Газировка", "price": 64},
        {"id": "004", "name": "Булочка", "price": 33},
    ]

    display_products(products)

    # Ввод ID товара
    product_id = input("Введите ID товара: ")
    
    # Проверка на существование товара
    product = next((p for p in products if p['id'] == product_id), None)
    if product is None:
        print("Товара с таким ID не существует")
        return

    price = product['price']
    print(f"Внесите {price} тугриков")

    total_inserted = 0

    while True:
        insert = input("Внесите купюру (или напишите 'ОТМЕНА' для выхода): ")

        if insert == "ОТМЕНА":
            print("Вы вышли из программы.")
            return

        # Проверка на валидность купюры
        if insert.isdigit() and int(insert) in {10, 50, 100, 500}:
            insert_amount = int(insert)
            total_inserted += insert_amount

            if total_inserted >= price:
                change = total_inserted - price
                print(f"Ваша сдача: {change} тугриков")
                return
            else:
                remaining = price - total_inserted
                print(f"Осталось внести {remaining} тугриков")
        else:
            print("Внесена фальшивая купюра")

if __name__ == "__main__":
    main()
    test3
    def main():
    while True:
        user_input = input("Введите номер задания (или 'выход' для завершения): ")

        if user_input.lower() == 'выход':
            break

        task_number = int(user_input)

        if task_number == 1:
            # 1. Фамилия и имя
            name = person[0].split()
            print(f"Персона: {name[1]}, {name[0]}")

        elif task_number == 2:
            # 2. Возраст Энакина
            print(person[1])

        elif task_number == 3:
            # 3. Места, связанные с крупными событиями
            events = ', '.join(person[2])
            print(events)

        elif task_number == 4:
            # 4. Количество мест
            print(len(person[2]))

        elif task_number == 5:
            # 5. Служит ли он Империи
            serves_empire = 'Звезда Смерти' in person[2]
            print(serves_empire)

        elif task_number == 6:
            # 6. Цвет светового меча
            light_saber_color = person[3]['световой меч']
            print(light_saber_color)

        elif task_number == 7:
            # 7. Изменение возраста
            person[1] = 42
            print(person[1])

        elif task_number == 8:
            # 8. Добавление места
            new_place = 'Эндор'
            if new_place not in person[2]:
                person[2].append(new_place)
            print(person[2])

        elif task_number == 9:
            # 9. Проверка ранга
            rank = person[3]['ранг']
            if rank == 'лорд ситхов':
                print("Энакин - лорд ситхов")
            else:
                print("Энакин - джедай")

        elif task_number == 10:
            # 10. Проверка количества мест
            if len(person[2]) > 4:
                print("Энакин побывал во многих местах")
            else:
                print("Энакин не так много путешествовал")

if __name__ == "__main__":
    main()
```
test4
# Исходный список компаньонов
companions = [
    "Astarion", "Gale", "Karlach", "Lae'zel",
    "Shadowheart", "Wyll", "The Dark Urge", "Halsin",
    "Jaheira", "Minsc", "Minthara", "Alfira", "Losiir"
]

# 1. ["Gale", "Karlach", "Lae'zel"]
first_slice = companions[1:4]
print(first_slice)

# 2. ["Gale", "Lae'zel", "Wyll", "Halsin", "Halsin", "Minsc", "Alfira"]
second_slice = companions[1:5] + companions[7:9] + companions[11:12]
print(second_slice)

# 3. ["Alfira", "Jaheira", "Wyll", "Karlach"]
third_slice = companions[11:12] + companions[8:9] + companions[5:6] + companions[2:3]
print(third_slice)

# 4. ["Astarion", "Losiir"]
fourth_slice = companions[0:1] + companions[12:13]
print(fourth_slice)
```
test5
```python
def main():
    valid_items = {"меч", "лук", "топор", "щит", "зелье"}
    chosen_items = []

    for adventurer in range(3):
        while True:
            items = input(f"Авантюрист {adventurer + 1}, выберите предметы через пробел: ").strip().lower().split()
            
            # Проверка на валидность введенных предметов
            if all(item in valid_items for item in items):
                chosen_items.append(set(items))
                break
            else:
                print("Неверный предмет, попробуйте снова")

    # Находим пересечение выбранных предметов
    common_items = set.intersection(*chosen_items)
    
    # Выводим количество общих предметов
    print(len(common_items))

if __name__ == "__main__":
    main()
```
test6
def main():
    # Начальные координаты Петра
    x, y = 0, 0

    # Считываем количество ходов
    n = int(input("Введите N: "))

    # Обработка каждого хода
    for i in range(n):
        direction = input(f"Ход {i + 1}: ").strip().lower()
        
        # Обновляем координаты в зависимости от направления
        if direction == "вверх":
            y += 1
        elif direction == "вниз":
            y -= 1
        elif direction == "вправо":
            x += 1
        elif direction == "влево":
            x -= 1

    # Рассчитываем кратчайшее расстояние до конечной точки
    shortest_path = abs(x) + abs(y)

    # Вывод результата
    print(shortest_path)

if __name__ == "__main__":
    main()
```
test7
def reverse_number(n):
    reversed_num = 0
    negative = n < 0  # Проверяем, отрицательное ли число
    n = abs(n)  # Работаем с положительным значением

    while n > 0:
        digit = n % 10  # Получаем последнюю цифру
        reversed_num = reversed_num * 10 + digit  # Добавляем цифру к результату
        n //= 10  # Убираем последнюю цифру

    return -reversed_num if negative else reversed_num

# Ввод числа
number = int(input("Введите целое число: "))
result = reverse_number(number)
print(result)
```
test8
def main():
    # Хранение структурированных данных о песне
    song_parts = {
        "куплет 1": "В истерике кружилась мама Валя\nНа заднем фоне замер папа Толя\nВ радиусе метра воцарился жесточайший хаос\nКогда всем понятно стало: сын остался без диплома",
        "припев": "Я выбираю — жить в кайф!\nЯ выбираю — жить в кайф!\nЯ выбираю — жить в кайф!\nЯ выбираю — жить в кайф!",
        "куплет 2": "Мама, не кричи, хватит плакать, не смей\nВдруг увидел солнце — и тогда себе я сказал:",
    }

    while True:
        user_input = input("Введите номер задания (1-3) или 'выход': ").strip().lower()

        if user_input == "выход":
            break

        if user_input == "1":
            part_name = input("Введите название элемента песни (куплет 1, припев, куплет 2): ").strip().lower()
            if part_name in song_parts:
                print(song_parts[part_name])
            else:
                print("Элемент песни не найден.")

        elif user_input == "2":
            full_text = "\n".join(song_parts.values())
            formatted_text = full_text.replace("[Куплет 1]", "").replace("[Припев]", "").replace("[Куплет 2]", "")
            print(f"<div style='text-align: center;'>{formatted_text.strip()}</div>")

        elif user_input == "3":
            word_count = {}
            # Собираем слова из всех частей песни
            all_text = "\n".join(song_parts.values()).lower()
            # Удаляем специальные символы
            cleaned_text = ''.join(c if c.isalnum() or c.isspace() or c == '-' else ' ' for c in all_text)

            # Подсчет слов
            words = cleaned_text.split()
            for word in words:
                word_count[word] = word_count.get(word, 0) + 1

            count_type = input("Введите 'куплет' для подсчета слов только из куплетов или 'песня' для полной песни: ").strip().lower()
            if count_type == "куплет":
                relevant_text = "\n".join([song_parts["куплет 1"], song_parts["куплет 2"]]).lower()
                cleaned_relevant = ''.join(c if c.isalnum() or c.isspace() or c == '-' else ' ' for c in relevant_text)
                words_relevant = cleaned_relevant.split()
                word_count_relevant = {}
                for word in words_relevant:
                    word_count_relevant[word] = word_count_relevant.get(word, 0) + 1
                # Сортировка и вывод 3 самых частых слов
                sorted_words = sorted(word_count_relevant.items(), key=lambda x: x[1], reverse=True)[:3]
            elif count_type == "песня":
                # Сортировка и вывод 3 самых частых слов
                sorted_words = sorted(word_count.items(), key=lambda x: x[1], reverse=True)[:3]
            else:
                print("Некорректный ввод.")
                continue

            for idx, (word, count) in enumerate(sorted_words, start=1):
                print(f"{idx}. \"{word}\" - {count} раз")

if __name__ == "__main__":
    main()
```
