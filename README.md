Python Pandas

Создание датафрейма:
df2 = pd.DataFrame({
   ...:         "A": 1.0,
   ...:         "B": pd.Timestamp("20130102"),
   ...:         "C": pd.Series(1, index=list(range(4)), dtype="float32"),
   ...:         "D": np.array([3] * 4, dtype="int32"),
   ...:         "E": pd.Categorical(["test", "train", "test", "train"]),
   ...:         "F": "foo",
   ...:     }
   ...: )
   
   
   Типы данных, хранимые в калонках:
   df2.dtypes
   
   Отобразить первые 10 значений датафрейма:
   df.head(10)
   
   Отобразить последние 10 значений датафрейма:
   df.tail(10)
   
   Отображение индексов:
   df.index
   
   Отображение колонок:
   df.columns
   
   Конвертирование датафрейма в массив numpy:
   df.to_numpy(dtype ='float32')
   
   Отображение статистик данных датафрейма:
   df.describe()
   
   Транспонирование данных в датафрейме:
   df.T
   
   Сортировка данных:
   df.sort_index(axis=1, ascending=False)
   
   Сортировка значений по столбцу:
   df.sort_values(by="B")
   
   Выборка:
   df["A"] - весь столбец
   df[0:3] - выборка по трем строкам
   
   Выборка loc - используется для доступа по строковой метке:
   df.loc[dates[0]] - выборка нулевой строки
   df.loc[:, ["A", "B"]] - выборка по столбцу "А" и "В"
   df.loc["20130102":"20130104", ["A", "B"]] - выборка по срезу значений индексов и по столбцам "А" и "В"
   df.loc[dates[0], "A"] - скалярное значения нулевого элемента столбца "А"
   df.at[dates[0], "A"] - скалярное значения нулевого элемента столбца "А" (быстрый доступ)
   
   Выборка iloc - используется для доступа по числовому значению (начиная от 0):
   df.iloc[3] - выборка четвёртой строки
   df.iloc[1, 1] - получение значения второй строки второго столбца
   df.iat[1, 1] - получение значения второй строки второго столбца (быстрый доступ)
   
   df[df["A"] > 0] - выборка всех строк, где значения по столбцу "А" больше 0
   
   df[df["E"].isin(["two", "four"])] - выборка строк по столбцу "Е" со значениями two и  four
   
   Добавление новой колонки в датафрейм:
   s1 = pd.Series([1, 2, 3, 4, 5, 6], index=pd.date_range("20130102", periods=6))
   df["F"] = s1
   
   Установка значения:
   df.at[dates[0], "A"] = 0 - установка значения в нулевой строке колонки "А" равного 0
   df.iat[0, 1] = 0 - позиционная установка значения в нулевой строке первой колонки равного 0
   
   df.loc[:, "D"] = np.array([5] * len(df)) - установка в колонке "D" значений всех строк, равных 5
   
   df2[df2 > 0] = -df2 - установка отрицательных значений элементов, где элементы больше нуля
   
   df1.dropna(how="any") - удаление всех строк, где присутствует хотя бы одно пропущенное значение в столбце
   
   df1.fillna(value=5) - заменить пропущенные элементы значением 5
   
   pd.isna(df1) - выводит маску со значениями False - где элементы не пропущены и True - где элементы пропущены
   
   Статистики:
   df.mean() - вывод среднего значения по столбцам
   df.mean(1) - вывод среднего значения по строкам
   
   Вычисление разницы между максимальным и минимальным значением в каждом столбце:
   df.apply(np.cumsum)
   df.apply(lambda x: x.max() - x.min())
   
   Вычисление повторяемость значений в столбце:
   pd.Series(np.random.randint(0, 7, size=10)) - серия из 10 элементов, заполненные случайными значениями от 0 до 7
   s.value_counts() - вывод значения и количества встречаемости этого значения
   
   Приведение всех строковых данных к нижнему регистру:
   s = pd.Series(["A", "B", "C", "Aaba", "Baca", np.nan, "CABA", "dog", "cat"])
   s.str.lower()
   
   Присоединение датафреймов:
   frames = [df1, df2, df3] - определяем, какие датафремы объеденить
   result = pd.concat(frames) - делаем слияние этих датафреймов
   
   Слияние датафреймов (как в SQL):
   pd.merge(left, right, on="key")
   
   Группировки:
   df.groupby("A").sum() - сгруппировать значения в колонке "А" и вывести сумму по остальным колонкам
   df.groupby(["A", "B"]).sum() - сгруппировать значения в колонке "А" потом по колонке "В" и вывести сумму по остальным 
   
   Создание сводных таблиц:
   pd.pivot_table(df, values="D", index=["A", "B"], columns=["C"])
   
   
   Категориальные данные:
   Переименование категориальных данных:
   df["grade"] = df["raw_grade"].astype("category")
   df["grade"] = df["grade"].cat.set_categories(["very bad", "bad", "medium", "good", "very good"])
   
   
   Сортировка значений:
   df.sort_values(by="grade")
   
   Выборка повторяемости значений категорий:
   df.groupby("grade").size()
   
   
   
   
   
   
   
   
   
   
   
   
