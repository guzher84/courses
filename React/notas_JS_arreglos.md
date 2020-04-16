[REGRESAR](readme.md)

---

## ForEach
>recorrer un arreglo

```
const arreglo = ['juan','pedro','raul];

let html = '';
arreglo.forEach(my_variable => {
    html += `<li> ${my_variable} </li>`;
})

```

## map

```
const arreglo = ['juan','pedro','raul];

arreglo.map( item => {
    return 'el nombre es '+ item;
});
```

## spread
>unir arreglos

```
let arreglo_1=['item01','item02','item03'];
let arreglo_2=['item04','item05'];

let arreglo_3 = [...arreglo_1,...arreglo_2];
```

## Filter
>filtrar arreglos

```
const personas = [
    {nombre: 'juan', edad: 23},
    {nombre: 'pedro', edad: 45},
    {nombre: 'raul', edad: 33}
];

//mayores de 30 años

const mayores = personas.filter(filtro =>{
    return filtro.edad > 30;
});
```

## Find
>buscar en arreglos

```
const personas = [
    {nombre: 'juan', edad: 23},
    {nombre: 'pedro', edad: 45},
    {nombre: 'raul', edad: 33}
];

//buscar juan

const juan = personas.find(filtro =>{
    return filtro.nombre === 'juan';
});
```

## reduce
>sumar en arreglos

```
const personas = [
    {nombre: 'juan', edad: 23},
    {nombre: 'pedro', edad: 45},
    {nombre: 'raul', edad: 33}
];

//sumatoria de edades

let edad_total = personas.reduce((edad_total, persona) =>{
    return edad_total + persona.edad;
});
```

---

[REGRESAR](readme.md)

