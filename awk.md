
Compara dois arquivos 

```awk '{ getline x<"file2" } $0!=x{ print x}' file1```

```getline x<"file2"```       passa a linha inteira do arquivo2 e mantém a variável x
```print x```                  quando a linha do arquivo1 for diferente da linha do arquivo2.

Ou

```awk '{ getline x<"file1" } $0!=x' file2```
