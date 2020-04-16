[REGRESAR](readme.md)

---

# **Componente**

1. en la carpeta /src/components
2. se crea un archivo Nombre_componente.jsx
```
import React from 'react';

const Footer = () => {
    return ( 
        <footer>
            <p>Todos los derechos Reservados &copy;</p>
        </footer>
    );
}
 
export default Footer;
```
3. en /src/App.js
```
import React, {Fragment} from 'react';
//componentes creados
import Header from './components/header'; 
import Footer from './components/footer';

function App() {
  return (
    <Fragment>
     <Header />

     <Footer />
    </Fragment>
  );
}

export default App;
```
---
## Paso de información entre componentes

en el componente padre

> para pasar tipos de datos que no sean cadenas se usan { }
```
function App() {

  const anio= new Date().getFullYear();
  return (
    <Fragment>
     <Header 
      Env='Prod'
      bandera={true}
     />

     <Footer 
      anio={anio}
     />
    </Fragment>
  );
}
```
en el componente hijo
>props es un obj que lleva la data
```
function Header(props){
    console.log(props);
    // *************colocar Código JavaScript *************
    const bandera = props.bandera;
```
>para no colocar props.parametros
```
const Footer = ({anio}) => {
    return ( 
        <footer>
            <p>Todos los derechos Reservados &copy; {anio}</p>
```
el dato recibido tiene que llamarse igual como lo estamos enviando en el componente padre

---
[REGRESAR](readme.md)

