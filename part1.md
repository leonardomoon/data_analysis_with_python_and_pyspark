- Notes:
  - In PySpark's world, a data frame is made out of `Column` objects, and you perform transformations on them.

- Useful functions:
  - select() and split():
    - ```python
      book.select(book["value"])
      ```
    - ```python
      book.select(col("value"))
      ```
    - ```python
      lines = book.select(split(book.value, " ").alias("line"))
      ```
  - explode(): reshaping data, exploding a list into rows
    -  ```python
        words = lines.select(explode(col("line")).alias("word"))
        ```
  - regexp_extract() and lower()
    - ```python
       words_lower = words.select(lower(col("word")).alias("word_lower"))
       ```
    - ```python 
       words_clean = words_lower.select(
            regexp_extract(col("word_lower"), "[a-z]+", 0).alias("word")
       )
      ```
