[REGRESAR](readme.md)

---
## **Estructura de un JSX**

```
import React from 'react';

function Header(){

    // *************colocar Código JavaScript *************
    const bandera = false;

    let titulo = '';

    if(titulo){
        titulo = 'Tienda Virtual';
    }else{
        titulo = 'Tienda Virtual (TEST)';
    }
    // *************colocar codigo Javascript *************

    // *************colocar codigo HTML y CSS*************

    //esto es lo que se vera en pantalla
    //para colocar valores de JS se necesita poner entre {}
    return(
        <h1 className="encabezado">{titulo}</h1>
    );
    // *************colocar codigo HTML y CSS*************
};

export default Header;
```

---
[REGRESAR](readme.md)

