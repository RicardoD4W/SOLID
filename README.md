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

En nuestro negocio todo va de maravilla y ahora queremos extender un poco más nuestro catalogo de productos, así que decidimos optar por empezar a vender ordenadores portátiles. Un atributo útil de un portátil es el tamaño de la pantalla integrada, pero como bien sabemos esto solo esta presente en los portátiles y no ordenadores de escritorio (generalizando), y sabiendo que JavaScript solo soporta una clase padre, podemos hacer esto:

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
