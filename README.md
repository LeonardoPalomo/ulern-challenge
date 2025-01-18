<h1>Instrucciones</h1>

<b>Prerrequisitos:</b>
Tener Composer y npm instalados.

<h2>Pasos:</h2>
1. En terminal, posicionarse adentro de la carpeta que contiene el repositorio (ej. escribir en terminal "cd ulern-challenge").<br />
2. Renombrar el archivo ".env.example" a ".env".<br />
3. Ejecutar en terminal las siguientes instrucciones uno por uno y esperar a que terminen:<br />
   - $<i>composer install</i><br />
   - $<i>npm install</i><br />
   - $<i>npm run build</i><br />
   - $<i>php artisan key:generate</i><br />
   - $<i>php artisan migrate</i> (responder "yes" a la pregunta)<br />
4. Por último, ejecutar en terminal $<i>php -S localhost:8000 -t public/</i><br />
5. Ingresar al navegador a la url "localhost:8000"<br />

<h2>Observaciones:</h2>

- En caso de que <i>php artisan migrate</i> presente errores, editar el archivo php.ini de la siguiente manera:
";extension=pdo_sqlite" debe ser "extension=pdo_sqlite". (https://stackoverflow.com/questions/38949781/pdo-exception-driver-not-found-in-laravel-for-sqlite/55144013#55144013)

- correr la aplicación utilizando <i>php artisan serve</i> puede presentar errores, en caso de ser así editar el archivo php.ini de la siguiente manera:
  "<b>variables_order = "EGPCS"</b>" debe ser "<b>variables_order = "GPCS"</b>"
