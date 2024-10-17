# Predicado com Listas: findall e setof

### Tanto a _findall_ quanto a _setof_ irão, a partir de uma base de dados, coletar as informações que satisfaçam uma condição e "retornar" os resultados em uma lista.

## Sintaxe no prolog: 
``` 
    findall(Template, Goal, Bag).
    setof(Template, Goal, Bag).
```
### Template: O que queremos extrair para a lista, geralmente uma variavel.
### Goal: condição que queremos satisfazer. 
### Bag: argumento que será armazenado os resultados que satisfazem o Goal.


## Findall:
  - coleta todas as possibilidades que satisfaçam o goal.
  - mantém duplicatas.
  - não ordena os resultados.
  - retorna uma lista vazia se não houver soluções.

```
parent(joao, maria).
parent(fernanda, maria).
parent(joao, jose).
parent(maria, joana).
parent(maria, marcela).
parent(jose, julia).

?- findall(Filhos, parent(Pais, Filhos), ListaFilhos).
ListaFilhos = [maria, maria, jose, joana, marcela, julia].
```

## Setof: 
  - coleta todas as possibilidades unicas que satisfaçam o goal.
  - remove duplicatas
  - ordena os resultados.
  - falha se não houver soluções.
  
```

?- setof(Filhos, Pais^parent(Pais,Filhos), ListaFilhos).
ListaFilhos = [joana, jose, julia, marcela, maria].

?- setof(Filhos, parent(Pais, Filhos), ListaFilhos).
Pais = fernanda,      
ListaFilhos = [maria] ;
Pais = joao,
ListaFilhos = [jose, maria] ;
Pais = jose,
ListaFilhos = [julia] ;
Pais = maria,
ListaFilhos = [joana, marcela].
```


### Referências: 

https://www.educba.com/prolog-findall/

https://lpn.swi-prolog.org/lpnpage.php?pagetype=html&pageid=lpn-htmlse49

https://www.youtube.com/watch?v=mFtEDoFIaxE
