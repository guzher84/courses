[REGRESAR](readme.md)

---

# Módulos

>importar y exportar JS

en el archivo js que va a exportar prueba_01.js  (**export**)
```
export const variable_x = 'prueba';

export const myFuncion = (tarea,urgencia) => {
    return `la tarea ${tarea} tiene una urgencia de ${urgencia}`;
};
```
en el archivo js que va a importar prueba_02.js  (**import**)
```
import { variable_x,myFuncion } from './prueba_01.js';

console.log(variable_x);
```
y para finalizar en nuestro index (**type="module"**)
```
<script scr="js/prueba_02.js" type="module"></script>
```

>exportar una clase

en un archivo tareas.js
```
export default class tarea{
    constructror(nombre, prioridad){
        this.nombre = nombre;
        this.prioridad = prioridad
    }
    mortar(){
        console.log(`${this.nombre} tiene una prioridad
                    de ${this.prioridad}`);
    }
}

```

en un archivo XXX.js
```
import Tarea from './tareas.js';

const tarea1 = new Tarea('Aprender JS','Alta');

tarea1.mostrar();
```

---

[REGRESAR](readme.md)

