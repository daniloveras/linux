
Compara dois arquivos 

```awk '{ getline x<"file2" } $0!=x{ print x}' file1```

```getline x<"file2"```       passa a linha inteira do arquivo2 e mantém a variável x
```print x```                  quando a linha do arquivo1 for diferente da linha do arquivo2.

Ou

```awk '{ getline x<"file1" } $0!=x' file2```

-----
```
cat file

US|A|1000|2000
US|B|1000|2000
US|C|1000|2000
UK|1|1000|2000
UK|1|1000|2000
UK|1|1000|2000
```
```
awk 'BEGIN { FS=OFS=SUBSEP="|"}{arr[$1,$2]+=$3+$4 }END {for (i in arr) print i,arr[i]}' file

US|A|3000
US|B|3000
US|C|3000
UK|1|9000
```
