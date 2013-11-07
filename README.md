README
======

Codigo en javascript para leer los save files de [pulmonear 2](http://www.duval.vg/foro/index.php?topic=1889.0).

Los tests están en test/SpecRunner.html

Desde index.html se puede cargar un save file y por consola se muestran los datos parseados.

Hay que tener en cuenta que no se chequean los valores pasados como índice a ```setNumero```, ```getNumero``` y ```setSwitch```, ```getSwitch```.


Uso
---

```
  var saveFile = new SaveFile();

  // setters
  saveFile.setFuturo( true / false );
  saveFile.setNumero( offset, valor );
  saveFile.setSwitch( offset, valor );
  saveFile.setNombre( nombre );
  saveFile.setData( data ); // un Array

  // getters
  saveFile.getFuturo();
  saveFile.getNumero( offset );
  saveFile.getSwitch( offset );
  saveFile.getNombre();
  saveFile.getData();

```

Se carga un archivo con

```
  saveFile.cargar( arrayBuffer );
```

El [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/API/ArrayBuffer) se puede generar a mano o a través de un file upload:

```
  <script>
  function cargarArchivo(file) {
    var reader = new FileReader();
    reader.onload = function(e) {
    	var saveFile = new SaveFile();
      	saveFile.cargar(e.target.result);

      	...
      	blah blah blah
      	...
    };

    reader.readAsArrayBuffer(file);
  }
  </script>
  
  <input id="uploadInput" type="file" onchange="cargarArchivo(this.files[0]);">
```

Probado en Chrome, Firefox y Safari

