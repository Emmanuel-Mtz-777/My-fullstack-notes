Los tipados son la mayor característica de [[Typescript ]] pero siempre que podamos hay que utilizar la inferencia de datos.
Pero aunque la inferencia de Typescript es muy buena si es necesario tipar los datos en algunos casos los cuales serian:
- ## Variables que reciben las funciones
```
function saludar (name:string){
	console.log(`Hola ${name}`)
}

const saludo=(name:string)=>{
	console.log(`Hola ${name}`)
}
```
- ## Datos de objetos
```
const persona:(name:string, age:number)={
	name:"Jose",
	age:12
}
```
Los objetos tienen tienen inferencia de datos excepto cuando se reutiliza el tipo.

- ## Objetos que reciben las funciones
La siguiente opción pasa el formato del objeto a demás de definir su tipado.
```
const saludo=({name,age}):{name:string, age:number}=>{
	console.log(`Hola ${name} tienes ${age} años`)
}
```
La siguiente opción pasa el objeto y su tipado y dentro de la función destructuramos el objeto para declarar las variables de una forma mas simple (Aunque también funciona la reestructuración pero deberíamos usar las variables como persona.name y persona.age)
```
const persona:(name:string, age:number)={
	name:"Jose",
	age:12
}

const saludar=(persona:{name:string, age:number})=>{
	const {name,age}=persona
	console.log(`Hola ${name} tienes ${age} años`)
}
```
De forma practica la primer opción es mas simple pero ambas funcionan.

- ## Callbacks
