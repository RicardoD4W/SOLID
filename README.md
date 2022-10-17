# Parte Medina


* [Principio de segregación de la interfaz (ISP)](#ISP)
* [Principio de inversión de la dependencia (DIP)](#DIP)



# ISP


<p>

<h3>
El principio nos indica que una clase debe de implementar únicamente las interfaces que necesita, es decir, que no necesite tener que implementar métodos que no utilice. Se aplica a una interfaz amplia y compleja para escindirla en otras más pequeñas y específicas, de tal forma que cada cliente use solo aquella que necesite.
</h3>

---

<p>

Imaginemos que tenemos un negocio de venta de ordenadores de escritorio, sabemos que todas las ordenadores deberían de extender de la clase Ordenador y tendríamos algo como esto:

<pre>
class Ordenador {
  marca;
  modelo;

  constructor(marca, modelo) {
    this.marca = marca;
    this.modelo = modelo;
  }

  obtenerMarca() {
    return this.marca;
  }

  obtenerModelo() {
    return this.modelo;
  }

  guardarMarca(marca) {
    this.marca = marca;
  }

  guardarModelo(modelo) {
    this.modelo = modelo;
  }
}

class Portatil extends Ordenador {
   ...
}
</pre>

En nuestro negocio todo va de maravilla y ahora queremos extender un poco más nuestro catalogo de productos, así que decidimos optar por empezar a vender ordenadores portátiles. Un atributo útil de un portátil es el tamaño de la pantalla integrada, pero como bien sabemos esto solo esta presente en los portátiles y no ordenadores de escritorio (generalizando), podemos hacer esto:

<pre>
  class Ordenador {
  marca;
  modelo;

  constructor(marca, modelo) {
    this.marca = marca;
    this.modelo = modelo;
  }

  obtenerMarca() {
    return this.marca;
  }

  obtenerModelo() {
    return this.modelo;
  }

  guardarMarca(marca) {
    this.marca = marca;
  }

  guardarModelo(modelo) {
    this.modelo = modelo;
  }
}

const Portatil = (clasePadre) => {
  return (
    class extends clasePadre {
      constructor(marca, modelo){
        super(marca, modelo);
      }

      guardarTamanioPantalla(tamanio) {
        this.tamanio = tamanio;
      }

      obtenerTamanioPantalla() {
        return this.tamanio;
      }

    }
  )
}
</pre>

</p>

</p>

---

# DIP


<p>
<h3>
En este principio se establecen que las dependencias deben de estar en las abstracciones y no en las concreciones, en otras palabras, nos piden que las clases nunca dependan de otras clases y que toda esta relación debe estar en una abstracción. Este principio tiene dos reglas:
</h3>

<pre>

   <h4> 1. Los módulos de alto nivel no deben de depender de módulos de bajo nivel. Esta lógica debe de estar en una abstracción. </h4>

   <h4> 2. Las abstracciones no deben de depender de detalles. Los detalles deberían depender de abstracciones. </h4>
</pre>
</p>

---

<p>
  
Imagina que tenemos una clase que nos permite enviar un correo:

<pre>
  class Correo {
  provider;

  constructor() {
    // Levantar una instancia de google mail, este código es con fin de demostración.
    this.provider = gmail.api.createService();
  }

  enviar(mensaje) {
    this.provider.send(mensaje);
  }
}

var correo = new Correo();
correo.enviar('hola!');

</pre>

En este ejemplo se puede ver que se está rompiendo la regla, puesto que la clase correo depende del proveedor de servicio, ¿qué pasaría si después queremos usar Yahoo y no Gmail?

Para solucionar esto debemos eliminar esa dependencia y añadirla como una abstracción.

<pre>
  class GmailProveedor {
  constructor() {
    // Levantar una instancia de google mail, este código es con fin de demostración.
    this.provider = gmail.api.createService();
  }
  enviar(mensaje) {
    this.provider.sendAsText(mensaje);
  }
}
class Correo {
  constructor(proveedor) {
    this.proveedor = proveedor;
  }
  enviar(mensaje) {
    this.proveedor.send(mensaje);
  }
}
var gmail = new GmailProveedor();
var correo = new Correo(gmail);
correo.enviar('hola!');

</pre>

De esta forma ya no nos importa el proveedor ni la forma en que implementa el envío de correos el proveedor, la clase de Correo solo se ocupa de una única cosa, pedirle al proveedor que envíe un correo.

</p>
