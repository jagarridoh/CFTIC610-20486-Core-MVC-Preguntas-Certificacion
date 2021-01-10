# Video Transcoding Service - Question 1
**QUESTION 1**

You are creating a new authentication system that uses an HTTP header value.
The existing authentication system must continue to operate normally.
You need to implement the custom authentication.

What should you do? (Each correct answer presents a complete solution. Choose all that apply.)

A. Create a class derived from ActionResult and check for a valid HTTP header value in the ExecuteResult
method. Change all actions to return this new class.
B. Create an HttpHandler to check fora valid HTTP header value in the ProcessRequest method.
C. Create an HttpModule and check for a valid HTTP header value in the AuthenticateRequest event.
D. Create a class derived from AuthorizeAttribute and check for a valid HTTP header value in the
AuthorizeCore method. Change usages of the existing AuthorizeAttribute to use the new class.

------

Correct Answer: CD
Section: (none)
Explanation
Explanation/Reference:
Explanation:

------

Comentarios:

* La pregunta hace referencia a autenticación y HTTP, por lo tanto, como en la descripción del escenario solo hay una aplicación web, la ASP .NET MVC situada en Azure, hemos de pensar que la autenticación existente se refiere a la de este sistema. No se nos describe en el escenario nada de la autenticación, salvo el atributo [Authorize] en el controller. Así pues podemos suponer que estamos ante la Simple Authorization tratada en el Módulo 11 del MOC.
* Respuesta A : ExecuteResult no aparece en los MOC 20486, 20483. Buscando en internet parece que no  va por el tema de la autenticación (https://docs.microsoft.com/en-us/dotnet/api/system.web.mvc.actionresult.executeresult?view=aspnet-mvc-5.2  -> Enables processing of the result of an action method by a custom type that inherits from the ActionResult class). Aún en el caso hipotético de que se pudiera avanzar por ahí, no parecería lo mejor tratar la autenticación mediante los objetos que entran en juego al final del proceso del controller. Convendría hacerlo al principio de la pipeline (middleware).
* Respuesta B : IHttpHandler ni ProcessRequest aparecen en los MOC 20486, 20483. Buscando en internet parecen referir a la base de tratar respuestas a peticiones web y no temas de autenticación. (https://docs.microsoft.com/en-us/dotnet/api/system.web.ihttphandler?view=netframework-4.8   https://docs.microsoft.com/en-us/dotnet/api/system.web.ihttphandler.processrequest?view=netframework-4.8)
* Respuesta C : HttpModule ni AuthenticateRequest aparecen en los MOC 20486, 20483. Buscando en internet HttpModule va en la línea correcta (https://www.infoworld.com/article/3090997/how-to-work-with-httpmodules-in-aspnet.html) y AuthenticateRequest también (https://docs.microsoft.com/en-us/dotnet/api/system.web.httpapplication.authenticaterequest?view=netframework-4.8).
* Respuesta D: en el LAB11 se usa AuthorizeAttribute.

