[REGRESAR](readme.md)

---

# REACT HOOKS
---

- Disponible desde la versión 16.8
- Permiten actualizar el state sin necesidad de crear un lcass component.
- La cantidad de código es menos.

## Hooks mas usados
|Básicos|Avanzados|
|:--:|:--:|
| useState | UseContext |
| useEffect | useRef |
|  | useReducer |
|  | useCallback |
|  | useMemo |

## USESTATE
se tiene que agregar en el import **{useState}**
```
import React, {useState} from 'react';
```
esta funcione al extraer sus valores cuenta con 2 partes:
```
const [clientes, guardarCliente] = useState([]);
```
- clientes = Tiene el state actual
- guardarCliente = cambia el state

### ejemplo useState

en el app.js agregamos el useState y los componentes a usar
```
import React, {Fragment,useState} from 'react';
import Producto from './components/producto';
import Carrito from './components/carrito';
```
agregamos 2 listados que usaran el useState
```
function App() {
  //crear listado de productos
  const [Arreglo, setProductos] = useState([
    {id:1,nombre:'camisa',precio:50},
    {id:2,nombre:'pantalon',precio:60},
    {id:3,nombre:'playera',precio:40}
  ]);
  //state para carrito de compras
  const [carrito,addProducto] = useState([])
```
pasamos los parametros y/o funciones que usaremos en cada componente

```
  return (
    <Fragment>
     <Header/>

     //se va realizar un ciclo, por cada elemento en nuestro arreglo
     //muy similar an un ngFor de angular
     
     <h2>Lista de Productos</h2>
     {Arreglo.map(item =>(
       <Producto 
          key={item.id}
          producto={item}
          productos={Arreglo}
          carrito={carrito}
          addProducto={addProducto}
         />
     ))}

     <Carrito
        carrito={carrito}
        addProducto={addProducto}
     />

     <Footer />
    </Fragment>
```
> si el componente D va a mandar a llamar al componente C, al componente D, se le pasan los parametros y/o funciones que el componente C va a usar, aunque el componente D no las use para nada

en este ejemplo, el componente carrito no va a usar addProducto, pero como Carrito, va a usar el componente Producto, es necesario pasarle esa funcion.

creamos el componente productos.jsx
```
import React from 'react'

const Producto = ({producto,carrito,addProducto,productos,flag_padre}) => {

    const {nombre, precio,id}=producto;

    const seleccionarProducto = (id) => {
        const my_item =productos.filter(item => item.id === id)[0];
        console.log(my_item);
        addProducto([
            ...carrito,
            my_item
        ]);
    };

    const eliminarProducto = (id) => {
        const my_item =carrito.filter(item => item.id !== id);
        console.log(my_item);
        addProducto(
            my_item
        );
    };

    return ( 
        <div>
            <h3>{nombre}</h3>
            <p>{precio}</p>

            { productos
            ?
                (<button
                type="button"
                onClick={() => seleccionarProducto(id)}
                >Comprar</button>)
            :
                (<button
                type="button"
                onClick={() => eliminarProducto(id)}
                >Eliminar</button>)
            }
        </div>
     );
}
 
export default Producto;
```

creamos un componente carrito.jsx
```
import React from 'react';
import Producto from './producto';
import './carrito.css'

const Carrito = ({carrito,addProducto}) => {
    return ( 
        <div className="carrito">
            <h2>Carrito de Compras</h2>
            {carrito.length === 0
            ?
                (
                    <p>No hay elementos en el carrito</p>
                )
            :    
                (
                    carrito.map(item =>(
                    <Producto 
                    key={item.id}
                    producto={item}
                    carrito={carrito}
                    addProducto={addProducto}
                    />
                    ))
                )
            }
        </div>
     );
}
 
export default Carrito;
```

---
[REGRESAR](readme.md)

