# Parte Juan


* [Principio de Responsabilidad Única](#SRP)


# SRP


<p>

<h3>    
El Principio de Responsibilidad única, del inglés "Single Responsibility Principle", dice que “una clase debería tener una, y solo una, razón para cambiar”. Es esto, precisamente, “razón para cambiar”, lo que Robert C. Martin identifica como “responsabilidad”.
</h3>
<br><br>
<h4>Beneficios del principio de responsabilidad única:</h4>

<pre>
   <h4> 1.- En relación al testing. Se simplifica 
        porque una clase tiene una única responsabilidad.. </h4>
   <h4> 2.- Se disminuye el acoplamiento pirque menor funcionalidad 
        en una clase hará que esta tenga menos dependencias. </h4>
   <h4> 3.- La organización de las clases y los paquetes 
        será mejor y más sencillo. </h4>
</pre>

---

<p>

<img width="auto" height="500px" src="/imgS/maluso.png" />
Esta clase UserLogin tiene como responsabilidad realizar el proceso de login pero además le dimos la responsabilidad de de enviar mensajes al usuario.
Este código viola el principio de responsabilidad unica. Está haciendo dos cosas con objetivos diferentes.
<br>

<img width="auto" height="500px" src="/imgS/buenuso.png" />
¿Entonces qué deberíamos hacer?

Sería conveniente separar la clase en dos. Una para lo específico del login y otra para la funcionalidad de envío de mensajes.


</p>



