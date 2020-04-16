[REGRESAR](readme.md)

---

## en el app.js
se agregan los imports
```
import React,{Fragment} from 'react';
import {useState} from 'react';
import {useEffect} from 'react';
import Formulario from './components/formulario';
import Cita from './components/Cita';
```
para el uso del localstorage
```
function App() {
  //citas en local storage
  let ArrayLocalStorage = JSON.parse(localStorage.getItem('citas'));
  if(!ArrayLocalStorage){
    ArrayLocalStorage = [];
  }

  //arreglo de citas
  const [arrayCitas,addCitas] = useState(ArrayLocalStorage);

  
  //useEffect observa cambios sobre el state
  useEffect(()=>{
    let ArrayLocalStorage = JSON.parse(localStorage.getItem('citas'));
    
    if(ArrayLocalStorage){
      localStorage.setItem('citas',JSON.stringify(arrayCitas));
    }
    else{
      //si el arreglo esta vacio se agrega un arreglo vacio
      localStorage.setItem('citas',JSON.stringify([]));
    }
  },[arrayCitas]);

```
las funciones que modifican el state
```
  //funcion que tome las citas actuales y tome la nueva
  const crearCita = (cita) =>{
    addCitas([
      ...arrayCitas, //sarcar copia del state
      cita
    ])
  };
  //funcion que elimina citas
  const EliminaCita= (id_cita) => {
    console.log("eliminar Cita"+id_cita);
    const nuevasCitas = arrayCitas.filter( item => item.id !== id_cita);
    addCitas(nuevasCitas);
  };

  //mensaje condicional
  const titulo = arrayCitas.length === 0 ? 'No hay citas' : 'Administra tus citas';
```
la parte HTML
```
  return (
    <Fragment>
      <h1>Citas</h1>

      <div className="container">
        <div className="row">
          <div className="col-sm-4">
            <Formulario
              crearCita={crearCita}
            />
          </div>
          <div className="col-sm-8">
            <h2>{titulo}</h2>
            
              {arrayCitas.map((item) =>(
                <Cita 
                  key={item.id}
                  cita={item}
                  EliminaCita={EliminaCita}
                />
              ))}
            
          </div>
        </div>
      </div>
    </Fragment>
  );
}

export default App;

```
---
## componente #1

se crea el componente formulario (formulario.jsx)
```
import React,{Fragment,useState} from 'react';
import uudi from 'uuid/v4'; //libreria para generar ID -> npm i uuid
import PropTypes from 'prop-types'; // para documentar el componente
```
en este formulario se tomaran los valores de los inputs y se almacenan en el state
```
const Formulario = ({crearCita}) => {

    //crear state citas
    const [cita,UpdateCita] = useState({
        mascota:'',
        propietario:'',
        fecha:'',
        hora:'',
        sintomas:'',
    });

    //state para manejo del error al no llenar los inputs
    const [error_inputs,UploadError] = useState(false);

    //función que se ejecuta cada vez que escribe en un input
    const actualizarState = e=>{
        //nombre del input
        //console.log(e.target.name);
        //valor de input
        //console.log(e.target.value);
        UpdateCita({
            ...cita, //sarcar copia del state
            [e.target.name]:e.target.value
        })
    }

    //extraer los valores
    const {mascota,propietario,fecha,hora,sintomas} = cita;

    //cuando se presiona el botón
    const ClickCita = (e)=>{
        //evita que se coloquen los datos en la url
        e.preventDefault();
        //validar
        if(mascota.trim() === '' || propietario.trim() === '' || fecha.trim() === '' 
        || hora.trim() === '' || sintomas.trim() === '' ){
            UploadError(true);
            return;
        }
        UploadError(false); //regresamos error_inputs a false
        //asignar ID
        cita.id = uudi(); //al obj cita le creamos un nuevo campo llamado id
        //crear cita
        crearCita(cita); //funcion que viene de App.js
        //reiniciar el form
        UpdateCita({
            mascota:'',
            propietario:'',
            fecha:'',
            hora:'',
            sintomas:''
        })
    };
```
la Parte HTML
```
    return ( 
      <Fragment>
        <h2>Crear</h2>
        { error_inputs
        ?
        <div className="alert alert-danger" role="alert">
            Todos los campos son requeridos
        </div>
        :
        null
        }

        <form
            onSubmit={ClickCita}
        >
            <div className="form-group">
                <label >Nombre de la Mascota</label>
                <input 
                    type="text" 
                    className="form-control" 
                    name="mascota" 
                    value={mascota}
                    onChange={actualizarState}
                    placeholder="Zapato" />
            </div>
            <div className="form-group">
                <label >Nombre del Dueño</label>
                <input 
                    type="text" 
                    className="form-control" 
                    name="propietario" 
                    value={propietario}
                    onChange={actualizarState}
                    placeholder="Juan" />
            </div>
            <div className="form-group">
                <label >Fecha</label>
                <input 
                    type="date" 
                    className="form-control" 
                    onChange={actualizarState}
                    name="fecha"
                    value={fecha} />
            </div>
            <div className="form-group">
                <label >Hora</label>
                <input 
                    type="time" 
                    className="form-control" 
                    onChange={actualizarState}
                    name="hora"
                    value={hora} />
            </div>
               <div className="form-group">
                <label >Sintomas</label>
                <textarea  
                    className="form-control" 
                    name="sintomas" 
                    value={sintomas}
                    onChange={actualizarState}
                    placeholder="Le duele la Pancita" >
                </textarea>
            </div>
            <button type="submit" className="btn btn-primary">Agregar Cita</button>
        </form>

      </Fragment>
    );
}
 ```
para documentar el componente 
 ```
//documentar
Formulario.propTypes={
    crearCita: PropTypes.func.isRequired
};
export default Formulario;
```
---
## componente #2
se crea el componente formulario (cita.jsx)
```
import React from 'react';
import PropTypes from 'prop-types'; // para documentar el componente
```

```
const Cita = ({cita,EliminaCita}) => {
    return ( 
        <div className="card bg-light mb-3" >
            <div className="card-header">{cita.mascota}</div>
            <div className="card-body">
                <h5 className="card-title">Dueño: {cita.propietario}</h5>
                <p className="card-text">Sintomas {cita.sintomas}.</p>
                <p className="card-text"><small className="text-muted">{cita.fecha} {cita.hora}</small></p>
            </div>
            <div className="card-footer bg-light">
                <button
                    type="button" 
                    className="btn btn-danger"
                    onClick={ () => EliminaCita(cita.id)}
                >Eliminar</button>
            </div>
        </div>
     );
}
```

```
//documentar
Cita.propTypes={
    cita: PropTypes.object.isRequired,
    EliminaCita: PropTypes.func.isRequired
};

export default Cita;
```

---
[REGRESAR](readme.md)

