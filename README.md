[//]: # (### Вариант 1)

[//]: # (<a href="https://imgbb.com/"><img src="https://i.ibb.co/5X1xnpS5/photo-2025-03-03-14-45-41.jpg" alt="photo-2025-03-03-14-45-41" border="0"></a>)
[//]: # (### Вариант 1)

<a href="https://imgbb.com/"><img src="https://i.ibb.co/KpH8bX9s/image-2025-03-03-14-50-42.png" alt="image-2025-03-03-14-50-42" border="0"></a>

# Проект KvantWars

Проект состоит из сайта и игры на нём.

## Структура

- venv - Виртуальное окружение проекта
- app - Папка с приложением

## Сайт
### Возможности:
1. На сайте у пользователя имеется возможность заполнить заявку на регистрацию и подать на одобрение администратору.

   Заявка состоит из следующих пунктов:
      - Логин
      - Пароль
      - ФИО
      - Возраст
      - Выбор фракции из списка существующих


2. Ресурсы
   Фракция может следить за своими ресурсами, доходами и т.п.


3. Действие
   - Фракция может совершить по одному каждому действию за ход
     - Захватить территорию (клетку)
     - Построить здание на своей территории
     - Улучшить построенное или завоёванное здание на своей территории
     - Защитить ячейку
     - Отправить ресурсы другой фракции

4. Логи
   У фракции есть возможность отслеживать что они сделали в этом ходу

## Игра
### Игровой процесс
1. Игра отображается на главной странице для всех, но взаимодействовать с ней могут только авторизированные члены фракции.
2. Ход общий для всех.
3. Ход в игре идёт 30 секунд (потом поменяем длительность на большее количество секунд).
4. Каждая фракция делает свои действия в течении хода, если фракция не сделала ход - засчитывается просто пропуск хода.
5. Итоги действий фракций подсчитываются в конце хода, там же начисляются ресурсы на следующий ход, в зависимости от построек фракции + стандартного дохода.

### Карта

Карта состоит из зелёных квадратов 7 на 7
1. Каждая фракция начинает в углу карты.
2. Каждый квадрат имеет серую обводку, если же квадрат принадлежит какой-то фракции, то цвет обводки меняется на цвет фракции.
3. Чтобы фракция могла захватить квадрат, этот квадрат должен быть соединён территорями до замка фракции.
4. Если фракция теряет территорию соединяющую ещё замок и остальные территории, то те анулируются и становятся свободными, постройки в таком случае не разрушаются, а просто становятся нейтральными.
5. Если фракция завоевывает территорию с постройкой, то постройка начинает принадлежать ей и приносить соответствующий доход от постройки.

### Фракции

На текущий момент в игре будет 4 фракции
- **IT-Квантум**
- **Design-Квантум**
- **Robo-Квантум**
- **Aero-Квантум**

У каждой будет свой основной цвет, который будет использоваться в игре в дальнейшем

### Ресурсы

В игре присутствую 5 видов ресурсов и их способ получения помимо стандартного дохода раз в ход:
- **Золото**: за каждую клетку, которой владеет фракиция.
- **Руда**: за каждую постройку, которая специализируется на данном ресурсе.
- **Камень**: за каждую постройку, которая специализируется на данном ресурсе.
- **Дерево**: за каждую постройку, которая специализируется на данном ресурсе.
- **Воины**: возможность купить за Золото.

#### Базовый прирост ресурсов

Определим базовый прирост ресурсов для каждой клетки. Это будет зависеть от типа ресурса и наличия соответствующих построек.

1. **Дерево**:
   - **Изначальное количество в начале игры**: 5 единиц.
   - **Базовый прирост**: 1 единица дерева в ход.
   - **Лесопилка**: увеличивает добычу дерева на 2 единицы за ход

2. **Руда**:
   - **Изначальное количество в начале игры**: 5 единиц.
   - **Базовый прирост**: 1 единица руды в ход.
   - **Шахта**: увеличивает добычу руды на 2 единицы за ход

3. **Камень**:
   - **Изначальное количество в начале игры**: 5 единиц.
   - **Базовый прирост**: 1 единица камня в ход.
   - **Карьер**: увеличивает добычу дерева на 2 единицы за ход

4. **Золото**:
   - **Изначальное количество в начале игры**: 10 единиц.
   - **Базовый прирост**: 2 единицы золота в ход.

5. **Воины**:
   - **Изначальное количество в начале игры**: 1 единицы.
   - **Базовый прирост**: отсутствует.

#### Найм и содержание воинов

Определим стоимость найма и содержания воинов.

1. **Найм воинов**:
   - **Стоимость найма одного воина**: 5 единиц золота.
   - **Максимальное количество воинов за один ход**: 10 воинов (зависит от количества доступного золота и построенных казарм).

2. **Содержание воинов**:
   - **Стоимость содержания одного воина в день**: 1 единица золота.
   - **Если у фракции не хватает золота для содержания всех воинов, то часть из них погибнет**.

### Постройки

В игре присутствуют следующие постройки со следующим функционалом:
- **Замок**: изначальная точка Фракции на карте (располагается в углу карты), присутствует в игре в единственном экземпляре на фракцию
- **Лесопилка**: увеличивает доход дерева за ход.
- **Шахта**: увеличивает доход руды за ход.
- **Карьер**: увеличивает доход камня за ход.
- **Склад**: увеличивает максимальный запас ресурсов у фракции. (даёт +20 к максимальному запасу всех ресурсов)
- **Казарма**: увеличивает максимальное количество воинов у фракции.

Так же нейтральные постройки защищаются N колличеством варваров

#### Улучшения построек и соответствующие бонусы

Мы можем улучшить любой вид постройки, кроме замка до 3-ёх уровней, изначально постройки имеют 1-ый уровень
   - Значок уровня улучшения находится слева сверху в клетке территории
   - Если постройка становится нейтральной, то становится 1-го уровня

Улучшения:
   - **Лесопилка**: каждое улучшение даёт +1 к доходу ресурса.
   - **Шахта**: каждое улучшение даёт +1 к доходу ресурса.
   - **Карьер**: каждое улучшение даёт +1 к доходу ресурса.
   - **Склад**:  каждое улучшение даёт +10 к максимальному запасу всех ресурсов.
   - **Казарма**:  каждое улучшение даёт +5 к максимальному количеству воинов у фракции.

### Точки интереса на карте и их защита варварами (ПОДУМАТЬ И СДЕЛАТЬ)

## Стек технологий
### Backend
- **Flask**
- **SQLAlchemy**
Возможны дополнительные библиотеки по ходу разработки

### Frontend
- **HTML + CSS + JS**
- **Bootstrap**
- **Jinja2**
