[REGRESAR](readme.md)

---

## Template String

Uso de ` para concatenar

```
let name = 'Juan';
let job = 'programador';

console.log('nombre:'+ name + ',Trabajo:'+ job);
console.log(`nombre: ${name} ,Trabajo: ${job}`);
```

### Truco 001

>se pueden usar el template string para colocar codigo HTML y mostrarlo

```
const contenedorApp = document.querySelector('#appName');

let cadena = `<H1>Titulo</H1>
            <h2>subtitulo<h2>
            `;

contenedorApp.innerHTML = cadena;
```

## function expression

```
const cliente = function(nombreCliente){
    console.log('Data: '+nombreCliente);
}

cliente('Juan');
```

## arrow functions

normalmente se haría así
```
let viajando = function(destino){
    return `Viajando a la ciudad de: ${destino}`;
}

let viaje = viajando('Puebla');

console.log(viaje);
```

con arrow function
```
let viajando = (destino) => {
    return `Viajando a la ciudad de: ${destino}`;
}

let viaje = viajando('Puebla');

console.log(viaje);
```

## object literal

```
const persona = {
    nombre: 'Juan',
    job: 'Desarrollador',
    edad: 23
}
```
para recuperar informacion
```
let edad = persona.edad;
let edad2 = persona['edad'];
```

## object constructor

```
function persona(nombre,job,edad)
{
    this.nombre: nombre,
    this.job: job,
    this.edad: edad
}

let person = new persona('juan','programador',23);
```

## prototype

```
function persona(nombre,job,edad)
{
    this.nombre: nombre,
    this.job: job,
    this.edad: edad
}

persona.prototype.mostrarInfo = function(){
    return `${this.nombre} trabaja como ${this.job} y tiene ${this.edad}`;
}

let person = new persona('juan','programador',23);

cosole.log(person.mostrarInfo());
```

## object destructuring

```
const persona = {
    nombre: 'Juan',
    apellido:{
        paterno:'guzman',
        materno:'herrera'
    }
    job: 'Desarrollador',
    edad: 23
}

let a_mat = persona.apellido.materno;
//declarado de otra manera
let {materno} = persona.apellido;
cosole.log(materno);
//mostrar herrera

let {apellido} = persona;
cosole.log(apellido);
//mostrara el objeto apellido
```

## object literal enhacement

```
const nombre = 'juan';
const nick = 'guzher';
const gustos = ['soccer','ps4'];

const my_obj = {nombre, nick, gustos};
```

## funciones en Obj
```
const persona = {
    nombre: 'Juan',
    edad: 23,
    mostrarInfo(){
        console.log(`${this.nombre} tiene ${this.edad} años`);
    }
}

persona.mostrarInfo();
```

## object Keys
>obtener los ids de una clase

```
const persona = {
    nombre: 'Juan',
    edad: 23,
}

console.log(Object.keys(persona));
```

---

[REGRESAR](readme.md)

