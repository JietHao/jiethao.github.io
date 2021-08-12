# LBYL与EAFP漫谈 (转：https://www.kawabangga.com/posts/3022)


- LBYL（Look before you leap.）

    - 指在程序执行之前做好检查。比如下面这段代码：
    ```python
    if "key" in my_dict:
        x = my_dict["key"]
    else:
        pass
    ```

    - 缺点：可能遗漏错误、可读性下降


- EAFP（Easier to ask for forgiveness than permission.）
    - 在编程方面指的是相信程序会正确执行，如果出错了再处理错误，比如上面这段代码用 EAFP 风格写就是下面这样：
    
    ```python
    try:
        x = my_dict["key"]
    except KeyError:
        pass
    ```
    
    - 优点：可读性更高、速度更快


- python推荐EAFP
- if不如直接raise
    ```python
    if not monitor_config.link:
        logger.error(f'{self} does not associate with link')
        return
    ```
- 选择
  - 如果EAFP没有副作用（原子性、事务、回滚等保障），则优先EAFP
  