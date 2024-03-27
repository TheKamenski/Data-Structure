1) Algorithms

2) C++

3) 273
```sh

find . -type f | wc -l
273 
```

4) 2,7M  .

```sh

du -sh .
2,7M	.
```

5) cpp 360612, hpp 508160, h 61742, cxx -, py 30871, pl -, php -, java -, cs -, rb -, rs -, hs -

```sh

find . -type f -name "*.cpp" -ls | awk '{sum+=$7} END {print sum}'
360612

find . -type f -name "*.hpp" -ls | awk '{sum+=$7} END {print sum}'
508160

find . -type f -name "*.h" -ls | awk '{sum+=$7} END {print sum}'
61742

find . -type f -name "*.cxx" -ls | awk '{sum+=$7} END {print sum}'

find . -type f -name "*.py" -ls | awk '{sum+=$7} END {print sum}'
30871

find . -type f -name "*.pl" -ls | awk '{sum+=$7} END {print sum}'

find . -type f -name "*.php" -ls | awk '{sum+=$7} END {print sum}'

find . -type f -name "*.java" -ls | awk '{sum+=$7} END {print sum}' 

find . -type f -name "*.cs" -ls | awk '{sum+=$7} END {print sum}'

find . -type f -name "*.rb" -ls | awk '{sum+=$7} END {print sum}'

find . -type f -name "*.rs" -ls | awk '{sum+=$7} END {print sum}'

find . -type f -name "*.hs" -ls | awk '{sum+=$7} END {print sum} 
pipe quote> 
```

6) Файл есть
```sh

find . -name ".clang-format"
```

7) Каталога нет

8) 0
```sh

grep -irl "socket" . | wc -l
0
```

9) 8
```sh

grep -irl "select" . | wc -l
8
```

10) 2
```sh

grep -ir -e "intel" -e "google" -e "microsoft" . | wc -l 
2
```

11) Файл есть
```sh

find . -type f -name "LICENSE" 
./LICENSE
```
12) Файл LICENSE имеется










