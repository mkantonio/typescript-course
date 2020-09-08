# Angular


## Typescript

Inicializar Typescript en la carpeta actual
`tsc --init`

Iniciar el observador de Typescript
`tsc -w
tsc --watch`

### Tipos de datos en Typescript

`
    let mensaje: string = 'Hola';
    let numero: number = 123;
    let booleano: boolean = true;
    let hoy: Date = new Date();

    // Any
    // let cualquiercosa 

    // Multiples tipos de datos para una variable
    let cualquiercosa: string | number | Date;

    let spiderderman = {
        nombre: 'Peter',
        edad: 20
    };

    spiderderman = {
        nombre: 'Juan',
        edad: 20
    };
`

### Template Strings
`
    function getEdad(){
        return 10+5+10;
    }

    const nombre = 'Yani';
    const apellido = 'Fuentes';
    const edad = 25;
    
    const salida = `${nombre} ${apellido} \n ${edad+100} \n (${getEdad()})`


    console.log(salida);
`
### Argumentos Typescript
Se debe espeficiar el tipo de dato de los argumentos en las funciones.
El orden de los argumentos debe de ser: obligatorios, opcionales y por defecto.

`
function activar(
    quien: string,
    momento?: string,
    objeto: string = "batiseñal",
  ) {
    //argumento 'momento' es opcional

    if (momento){
        console.log(`${quien} activo la ${objeto} en la ${momento}`);
    }else{
        console.log(`${quien} activo la ${objeto}`);
    }   
  }

  activar('Gordon', 'tarde');
`

### Funciones flecha
Es una nueva forma de escribir las funciones en ES6 (EcmaScript2015), pero con la mejora de que las funciones flecha no cambian el contexto de <b>this</b>

`

    const miFuncion = function(a: string){
        return a.toUpperCase;
    }

    const miFuncionFlecha = (a: string) => a.toUpperCase;

    const sumarN = function(a: number, b: number){
        return a+b;
    }

    const sumarNF = (a: number, b: number) => a+b;


    const hulk = {
        nombre: 'Hulk',
        smash(){
            setTimeout( () =>{
                console.log(`${this.nombre} smash!!!`);
            },1000);
        }
    }
    
`

### Desestructuración de objetos
`
    const avenger = {
        nombre: 'Steve',
        clave: 'Capitan America',
        poder: 'Droga'
    }
    
    const { nombre, clave, poder } = avenger;
    console.log( nombre );
    console.log( clave );
    console.log( poder );

    
    const extraer = ( {nombre, poder}: any ) =>{
        console.log( nombre );
        console.log( poder );
    }

    const avengers2: string[] = ['Thor', 'Ironman', 'Spiderman', 'liebre'];
    const [loki, hombre, , animal] = avengers2;

    console.log( loki );
    console.log( hombre );
    console.log( animal );

    const extraerArr = ( [thor, ironman, spiderman]: string[] ) =>{
        console.log( thor );
        console.log( ironman );
        console.log( spiderman );
    }
    extraerArr( avengers2 );
`

### Promesas
`    console.log('Inicio')
    const prom1 = new Promise( (resolve, reject) => {

        setTimeout(() => {
            resolve('Se termino el timeout');
            // reject('Se termino el timeout');
        }, 1000);

    })

    prom1
    .then( mensaje => console.log( mensaje ))
    .catch( err => console.warn( err ));

    console.log('Fin')`

ejemplo de promesas indicando el tipo de dato
`    const retirarDinero = ( montoRetirar: number ): Promise<number> => {
        let dineroAtual = 1000;

        return new Promise((resolve, reject) => {
            
            if (montoRetirar > dineroAtual){
                reject('No hay suficientes fondos');
            }else{
                dineroAtual -= montoRetirar;
                resolve( dineroAtual );
            }
        });

    }

    retirarDinero(500)
    .then( montoActual => console.log(`Me queda ${ montoActual }`) )
    .catch( err => console.warn( err ) );`

    ### Interfaces
    Las interfaces son como clases tontas, que no tienen métodos, solo se definen los atributos.
    Las interfaces son una forma de definir reglas si se desea utilizar un objeto determinado.  

    `interface Xmen {
        nombre: string;
        edad: number;
        poder?: string;
    }

    const enviarMision = ( xmen: Xmen ) => {

        console.log(`Enviando a ${xmen.nombre} a la mision`);
    } 
    const regresarAlCuartel = ( xmen: Xmen ) => {
        console.log(`Enviando a ${xmen.nombre} al cuartel`);
    }

    const wolverine = {
        nombre: 'Logan',
        edad: 60
    }
    
    enviarMision(wolverine);
    regresarAlCuartel(wolverine);`

    ### Clases
    `    
    class Avenger {

        constructor( public nombre: string,
                    public equipo: string,
                    public nombreReal?: string,
                    public puedePelear: boolean = true,
                    public peleasGanadas: number = 0){}
    }

    const antman = new Avenger('Antman', 'Capi');
`
### Funciones con tipo de dato
`
const sumar = (a: number, b: number): number => a+b;
const nombre = (): string => 'Hola Angular';
const obtenerSalario = (): Promise<string> => {
    return new Promise( (resolve, reject) => {
        resolve('Angular course');
    })
}

    obtenerSalario().then( a => console.log(a.toUpperCase()))
`