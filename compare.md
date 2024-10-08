### 1. Описание задачи

Задача заключается в модернизации узла связи в антивандальном шкафу 42U, с целью обеспечения длительного времени автономной работы (около 10 часов) за счет резервного питания от аккумуляторов. На данный момент, оборудование питается от сети 220 В через ИБП **Inelt 500**. В проекте нужно учесть следующие моменты:
- Установка мощного ИБП, поддерживающего внешние аккумуляторы.
- Обеспечение безопасности системы (предохранители, защита от перегрузки).
- Размещение оборудования и аккумуляторов в стойке 42U.
- Расчет времени автономной работы и выбор оптимальной схемы питания (24 В, 48 В или 220 В).

---

### 2. Расчеты токов потребления

#### Активное оборудование узла связи:
- **Коммутатор Eltex MES2124M**: ~24 Вт
- **Сервер SuperMicro с процессором Xeon E3-1230 v2**: ~80 Вт
- **5 Ubiquiti UniFi AP**: ~25 Вт
- **GPON OLT BDCOM P3310**: ~40 Вт
- **Микротик RB4011**: ~18 Вт
- **TP-Link TL-MR3020**: ~3 Вт
- **Итого**: ~210 Вт

#### Ток потребления для расчета времени автономности:
- Средняя суммарная мощность: **210 Вт**
- Напряжение ИБП: **220 В**

---

### 3. Аккумуляторы и резервное питание

Для обеспечения автономной работы планируется использовать два аккумулятора **12 В, 125 А·ч**, соединенные последовательно для получения **24 В**, а также подходящий ИБП для управления резервным питанием.

- Общая емкость АКБ:  
  \( 24 \text{ В} \times 125 \text{ А·ч} = 3000 \text{ Вт·ч} \)
  
- Оборудование потребляет 210 Вт. Время автономной работы:
  \[
  \frac{3000 \text{ Вт·ч}}{210 \text{ Вт}} = 14.3 \text{ часов}
  \]
  
Этого достаточно для выполнения задачи по автономности.

#### ИБП для стойки:

Мы выбрали несколько вариантов ИБП, подходящих для задачи:

1. **APC Smart-UPS SRT 2200 RMXLI**  
   - Мощность: 2200 ВА / 1980 Вт
   - Поддержка внешних АКБ для расширения времени автономной работы.

2. **Eaton 5PX 2200i RT2U**  
   - Мощность: 2200 ВА / 1980 Вт
   - Поддержка внешних АКБ.

3. **Powercom VRT-2000RM**  
   - Мощность: 2000 ВА / 1400 Вт  
   - Более бюджетный вариант, поддержка внешних батарей.

---

### 4. Монтаж оборудования в шкаф 42U

Расположение оборудования в шкафу 42U:
1. **1U** — Оптический кросс.
2. **2U** — Кабельный органайзер.
3. **3U** — Патч-панель RJ-45.
4. **4U** — Кабельный органайзер.
5. **5U** — Коммутатор Eltex MES2124M.
6. **6U** — GPON OLT BDCOM P3310.
7. **7-8U** — Сервер SuperMicro.
8. **9U** — MikroTik RB4011.
9. **10U** — Резервный юнит (под второй коммутатор).
10. **11U** — Полка для медиаконвертеров.
11. **12-23U** — Пустые юниты для будущего оборудования.
12. **24-30U** — Установка ИБП и АКБ.

Для аккумуляторов потребуется минимум **6 юнитов**. ИБП разместится рядом с аккумуляторами в одном из пустых юнитов (2U).

---

### 5. Обеспечение защиты и кабельная разводка

#### Защита:
- **Автомобильные предохранители** (на АКБ) — для защиты от перегрузок.
- **Клеммные соединения** — для распределения питания.
- **Кабель ПВ3** — для соединений между аккумуляторами и оборудованием:
  - Основные линии (питание АКБ): сечение 10 мм².
  - Подключение нагрузки: сечение 1.5-4 мм².

#### Кабельная разводка:
- Основные силовые кабели от АКБ к ИБП и от ИБП к оборудованию будут проводиться через клеммные коробки с использованием прессованных клемм и болтовых соединений для надежности.

---

### 6. Калькуляция необходимого оборудования и материалов

| Позиция                           | Количество | Примерная цена (руб) | Общая стоимость (руб) |
|------------------------------------|------------|----------------------|-----------------------|
| ИБП (APC Smart-UPS SRT 2200 RMXLI) | 1 шт       | 120 000              | 120 000               |
| АКБ 12 В, 125 А·ч (Delta HR 12-125)| 2 шт       | 35 000               | 70 000                |
| Автомобильные предохранители 80 А  | 2 шт       | 300                  | 600                   |
| Клеммные коробки                   | 2 шт       | 1 000                | 2 000                 |
| Кабель ПВ3, 10 мм²                 | 10 м       | 400                  | 4 000                 |
| Кабель ПВ3, 4 мм²                  | 20 м       | 200                  | 4 000                 |
| Пресс-клеммы                       | 20 шт      | 50                   | 1 000                 |
| Розетки и монтажные материалы      | -          | -                    | 5 000                 |

**Итого**: ~206 600 руб.

---

### 7. Примерная стоимость компонентов для модернизации

- ИБП: 120 000 руб.
- АКБ: 70 000 руб.
- Прочие компоненты и монтаж: ~16 600 руб.

Общая стоимость модернизации: **~206 600 руб**.

---

### 8. Перечень материалов и оборудования для модернизации узла связи

1. **ИБП для стойки (APC, Eaton, Powercom)** — 1 шт.
2. **Аккумуляторы 12 В, 125 А·ч (2 шт)** — Delta, Ritar или аналог.
3. **Автомобильные предохранители** (80 А) — 2 шт.
4. **Клеммные коробки** — 2 шт.
5. **Кабель ПВ3, сечение 10 мм²** — 10 м.
6. **Кабель ПВ3, сечение 4 мм²** — 20 м.
7. **Пресс-клеммы и соединительные элементы**.
8. **Розетки и монтажные материалы**.

---

### 9. Выводы

Сравним три варианта систем питания (24 В, 48 В и 220 В) с точки зрения времени автономности, стоимости и сложности реализации:

| Параметры             | Система 24 В       | Система 48 В       | Система 220 В        |
|-----------------------|--------------------|--------------------|----------------------|
| **Время автономности** | ~9 часов           | ~28 часов          | ~14 часов            |
| **Стоимость**          | ~250 000 руб       | ~270 000 руб       | ~206 600 руб         |
| **Сложность**          | Средняя            | Высокая            | Низкая               |
| **Возможность генератора** | Проблематично      | Проблематично      | Легко подключить     |


### Итог:
- **220 В система** с ИБП и АКБ является наиболее простым и универсальным решением.
- Система на **24 В** обеспечивает меньшее время автономности, но является энергоэффективной для маломощных объектов.
- **48 В система** подходит для более сложных объектов, где требуется высокая автономность, но ее реализация сложнее и дороже.

Система на 220 В с ИБП является наилучшим выбором по соотношению затрат, времени автономности и простоты реализации.