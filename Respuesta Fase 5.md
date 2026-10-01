# Respuesta Fase 5

## 1. ¿Por qué Git ha sido capaz de fusionar de forma automática los cambios del Alumno A y del Alumno B sin dar ningún error de conflicto?

Git utiliza algoritmos de fusión (*merge*) inteligentes. Ha podido realizar la fusión automáticamente porque:

* **Modificaron partes/líneas distintas del archivo** (o archivos diferentes).
* Git analiza los cambios línea por línea partiendo de un commit común. Si las modificaciones no se solapan en las mismas líneas de texto, Git comprende cómo integrar ambos cambios sin ambigüedad y realiza el merge automático (*Auto-merging*).

---

## 2. ¿Qué habría pasado si ambos hubiéramos intentado modificar la misma línea de texto a la vez?

Si ambos intentan modificar exactamente la **misma línea** (o las mismas líneas adyacentes) con contenidos diferentes y enviar los cambios a la misma rama:

1. **Conflicto de fusión (*Merge Conflict*):** Git no puede determinar cuál de las dos versiones es la correcta, por lo que **detiene la fusión** automáticamente y genera un aviso de conflicto.
2. **Marcas de conflicto en el archivo:** Git modificará el archivo afectado insertando marcas visuales para delimitar los cambios de cada uno:
   ```text
   <<<<<<< HEAD
   Cambio realizado por el Alumno A
   =======
   Cambio realizado por el Alumno B
   >>>>>>> nombre-de-la-otra-rama
   ```
3. **Resolución manual:** Es necesario abrir el archivo, decidir qué cambio conservar (o redactar uno combinado), eliminar las marcas de conflicto (`<<<<<<<`, `=======`, `>>>>>>>`), guardar los cambios y hacer un `git commit` para finalizar la fusión.
