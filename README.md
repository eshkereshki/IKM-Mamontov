# Проект: Министерство чиновников

## Описание проекта
Данный проект представляет собой программу на Python для расчета минимальной суммы взяток, необходимой предпринимателю для получения лицензии в министерстве. Иерархия министерства представлена в виде дерева, где каждый чиновник (кроме главного) имеет одного начальника и может иметь несколько подчиненных. Для получения подписи главного чиновника требуется собрать подписи по цепочке подчиненных, при этом каждый чиновник требует либо взятку, либо подпись хотя бы одного из своих подчиненных.

## Автор
- ФИО: Мамонтов Станислав Игоревич
- Группа: ИТ-9

## Требования
- Python 3.6+
- Для работы программы не требуются внешние зависимости
- Код соответствует PEP 8
- Использованы принципы ООП (инкапсуляция, композиция)

## Структура проекта
Проект состоит из двух основных классов:
1. `OfficialNode` - представляет чиновника с:
   - ID
   - Размером взятки
   - Списком подчиненных
2. `MinistryHierarchy` - управляет иерархией чиновников и содержит методы для:
   - Добавления новых чиновников
   - Валидации входных данных
   - Расчет минимальной суммы взяток
   - Построения оптимального пути подписей

## Алгоритм работы
1. Пользователь добавляет чиновников через консольный интерфейс, указывая:
   - ID чиновника
   - Размер взятки
   - ID начальника (0 для главного чиновника)
2. Программа строит иерархию чиновников как дерево
3. При запросе расчета программа рекурсивно обходит дерево, вычисляя:
   - Для чиновников без подчиненных - только их взятку
   - Для чиновников с подчиненными - минимальную сумму между:
     * Только их взяткой
     * Суммой их взятки и минимальной взятки среди подчиненных
4. Результат выводится в виде:
   - Общей минимальной суммы
   - Оптимального пути сбора подписей

## Инструкция по использованию
1. Запустите программу: `CODE_.py`
2. В главном меню выберите:
   - 1: Добавить чиновника (формат: "ID,взятка,ID_начальника")
   - 2: Просмотреть всех добавленных чиновников
   - 3: Рассчитать минимальную взятку и оптимальный путь
   - 4: Выйти из программы

## Пример работы
- Пример 1:
  - Ввод: 1,10000,0
  - Вывод: Чиновник 1 успешно добавлен
- Пример 2:
  - Ввод: Пункт меню (2)
  - Вывод: ID: 1, Взятка: 10000.0 у.е., Подчинённые: нет
- Тест на ошибку:
  - Ввод: 1(ID),-10000(Взятка),0(Начальник)
  - Вывод: Ошибка: Взятка должна быть числом (целым или дробным)

## Примечания
Исходный код доступен в этом репозитории.
