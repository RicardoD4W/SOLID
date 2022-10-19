# Parte Juan


* [Principio de Responsabilidad Única](#SRP)


# SRP


<p>

<h3>    
El primer principio de SOLID llamado Principio de Responsabilidad Única indica que una clase debería ser responsable de una única funcionalidad. En otras palabras, la clase solo debería tener una única razón para cambiar.
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
<h3>Mal uso</h3>
<img width="auto" height="400px" src="/imgS/maluso.png" />
<br>
Esta clase UserLogin tiene como responsabilidad realizar el proceso de login pero además le dimos la responsabilidad de de enviar mensajes al usuario.
Este código viola el principio de responsabilidad unica. Está haciendo dos cosas con objetivos diferentes.
<br>
<h3>Buen uso</h3>
<img width="auto" height="250px" src="/imgS/buenuso.png" />
<br>
¿Entonces qué deberíamos hacer?

Sería conveniente separar la clase en dos. Una para lo específico del login y otra para la funcionalidad de envío de mensajes.


</p>



