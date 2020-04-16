[REGRESAR](readme.md)

---

## Promesas
>llamados asincronos a funciones

```
const aplicarDescuento = new Promise ((resolve, reject)=>{
    let descuento = true;

    if(descuento){
        resolve('con descuento');
    }
    else{
        reject('sin descuento');
    }
});

aplicarDescuento.then(variable => {
    console.log(variable);
}).catch(error => {
    console.log(error);
});

```

### Promises con AJAX
```
const DescargaUsuarios = cantidad => new Promise((resolve, reject =>{
    const api = 'URL';
    const xhr = new XMLHttpRequest();

    xhr.open('GET', api, true);

    xhr.onload = () => {
        if(xhr.status === 200){
            resolve( JSON.parse(xhr.responseText).results);
        }
        else{
            reject(Error(xhr.statusText));
        }
    };

    xhr.onerror = (error) => reject(error);

    xhr.send();

});

DescargaUsuarios(30)
    .then(
        miembros => console.log(miembros),
        error => console.erro(
            new error('hubo error' + error)
        )
    );
```

---

[REGRESAR](readme.md)

