[REGRESAR](readme.md)

---

# Básico

## CREATE REACT APP  
### WEBPACK
es un bundler (paquete) de modulos para aplicaciones JS modernas, webpack procesa la aplicacion y matea todas las dependencias de un modulo, con esto crea uno o varios paquetes o bundlers.

Ademas de transpilar codigo JS moderno a versiones anteriores atraves de **babel**.

## crear ambiente

en la terminal
```
npx create-react-app Nombre_Proy
```

mover a la capeta
```
cd Nombre_Proy
```

correr el proyecto
```
npm start
```

>servidor de react http://localhost:3000/
---
## CREAR BUILD

```
npm run build
```
crea una carpeta llamada build

## Estructura
- node_modules
- public
    - aqui se coloca todo lo que tiene acceso publico
- src
    
    index.js
        
        archivo mas importante del proyecto
            
        ReactDOM.render([que va a mostrar], [en donde lo va a mostrar]);
        ReactDOM.render(<App />, document.getElementById('root'));
    
    App.js
        
        este es un componente

## Condición 
```
            { condicion
            ?
                ( html a mostrar cuando se cumple)
            :
                ( html a mostrar cuando no se cumple)
            }
```
ejemplo
```
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
```

## Recorrer elementos

```
  //crear listado de productos
  const [Arreglo, setProductos] = useState([
    {id:1,nombre:'camisa',precio:50},
    {id:2,nombre:'pantalon',precio:60},
    {id:3,nombre:'playera',precio:40}
  ]);
```
```
     {Arreglo.map(item =>(
       <Producto 
          key={item.id}
          producto={item}
          productos={Arreglo}
          carrito={carrito}
          addProducto={addProducto}
         />
     ))}
```

---
[REGRESAR](readme.md)



