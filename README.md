<h1><bold>Api conversion de xml a json</bold></h1>

corre en localhost:4300/converter/"url-a-convertir" (las " no van no seas...)

Recibe como parametro una url o un archivo xml y lo convierte a json y viceversa.
La url no necesita ser normalizada para realizar la conversión.

Es peligroso ir solo, toma esto:

```
de xml a json:
localhost:4300/converter/http://portalgeo.sernageomin.cl/geoportal/rest/find/document?searchText=araucania

de json a xml
localhost:4300/converter/https://jsonplaceholder.typicode.com/posts

```

No tienes que preocuparte de nada es suficientemente inteligente para saber diferenciar entre un xml y json 
y hacer la conversion adecuada.

para entregarle el archivo debes usar localhost:4300/upload, el nombre del input debe ser "file".

Para asegurame de que no tengas que ir a stack overflow te dejare esto:
```html
<form action='http://localhost:4300/upload' method="POST" enctype="multipart/form-data">
  <input type="file" class="col-6" name="file">
  <button type="submit">Subir...</button>
</form>
```
Así tambien me aseguro de no ver tu rostro en las cajas de leche despues:
el comando de ejecucion es npm run start-dev para correrla en modo desarrollo.
```
WARNING!!! WARNING!! WARNING!!!

cada vez se modifique la api recomiendo correr: npm run build
así tendras siempre la ultima version de los js compilada en la carpeta lib.
```

en modo produccion ejecuta npm run start-production


node 8.11 + typescript 3.3 + nodemon 1.8.1

algo no menos importante: TS y ts-node deben estar instaldos de manera global.

<h1><bold>CONSUMIR DESDE HEROKU</bold></h1>

Bien ahora tambien puedes ir y consumir el servicio comodamente... 

para ello solo debes consumir esta url: 
```
https://api-bidireccional-xml2json.herokuapp.com/converter/

para asegurame te llevare de la mano

https://api-bidireccional-xml2json.herokuapp.com/converter/geoportal/rest/find/document?searchText=arica

te entregara el json equivalente 

(OJO MÁS ABAJO HAY INFO QUE PODRIA INTERESARTE PARA CONVERTIR JSON A XML DE MANERA CORRECTA, 
APLICA TANTO PARA EL USO DE ARCHIVOS COMO PARA EL CONSUMO DE LA API VIA URL).

https://api-bidireccional-xml2json.herokuapp.com/converter/https://jsonplaceholder.typicode.com/posts

te entregara el xml correspondiente
```
Olvide mencionarlo, esta api permite la escritura de CDATA :D

Shinji usa POSTMAN o rei tendra que hacerlo de nuevo!!

si quieres subir archivos json o xml :
```
https://api-bidireccional-xml2json.herokuapp.com/upload

PRO TIPS PARA LA CONVERSION DE JSON A XML:

agregando atributos xmlns: 

{ 
  Foo: {
    $: {
      "xmlns": "http://foo.com"
    }   
  }
};  

entrega:

<Foo xmlns="http://foo.com"/>

Ejemplo de declaracion de nombres de espacio que no son por defecto:

{
  'foo:Foo': {
    $: {
      'xmlns:foo': 'http://foo.com'
    },
    'bar:Bar': {
      $: {
        'xmlns:bar': 'http://bar.com'
      }
    }
  }
}
resultado:

<foo:Foo xmlns:foo="http://foo.com">
  <bar:Bar xmlns:bar="http://bar.com"/>
</foo:Foo>
```
No tienes que preocuparte por declarar los objetos, solo tienes que preocuparte de que el json este bien escrito,
yo hago el JSON.parse() por ti :D

de todas maneras si qieres mas info para mejorar o customizar esta api : https://github.com/Leonidas-from-XIV/node-xml2js
Con gusto acepto coperacion para mejorarla aun mas.

Pero cuidado aun no implemento nada que borre los archivos, es un punto pendiente... me puedo quedar con todos tus secretos :3

