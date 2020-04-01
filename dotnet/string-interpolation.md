https://docs.microsoft.com/pt-br/dotnet/csharp/tutorials/string-interpolation

Interpolação ou *Interpolação de cadeias de caracteres como diz na docs* é, em resumo, uma técnica para concatenar strings com valores de variáveis de forma mais legível.

*Importante não esquecer de adicionar o cifrão no início.*

**Concatenação:**
```
  int userId = 1;
  _client.Get("api/Users/" + userId);
```


**Interpolação:**
```
  int userId = 1;
  _client.Get($"api/Users/{userId}");
```

Obs. 1: Neste link https://www.meziantou.net/performance-string-concatenation-vs-string-format-vs-interpolated-string.htm foi feito um benchmark comparando a performance entre diferentes técnicas de concatenatação de strings.
