[REGRESAR](readme.md)

---

# Programación Orientada a Objetos

## Clases

```
class Tarea{
    constructor(nombre, prioridad){
        this.nombre = nombre;
        this.prioridad = prioridad;
    }

    mostrar() {
        return `${this.nombre} tiene una prioridad de ${this.prioridad}`;
    }
}

let tarea1 = new Tarea('lavar auto','baja');

console.log(tarea1.mostrar());
```

## Herencia

```
class Tarea{
    constructor(nombre, prioridad){
        this.nombre = nombre;
        this.prioridad = prioridad;
    }

    mostrar() {
        console.log() `${this.nombre} tiene una prioridad de ${this.prioridad}`);
    }
}

class Compras extends Tarea {
    constructor(nombre, prioridad, cantidad){
        super(nombre, prioridad);
        this.cantidad = cantidad;
    }
    mostrar() {
        super.mostrar();
        console.log() `y la cantidad de ${this.cantidad}`);
    }
}

let compra1 = new Compras('Jabon','baja',3);

compra1.mostrar();
```
---

[REGRESAR](readme.md)

