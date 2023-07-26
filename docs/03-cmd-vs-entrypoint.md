## CMD vs ENTRYPOINT

- Tanto _CMD_ como _ENTRYPOINT_ son directivas utilizadas en el Dockerfile para definir el comando predeterminado que se ejecutará cuando se inicie un contenedor.
- Generalmente se usa _ENTRYPOINT_ para apuntar a la aplicación principal que se desea ejecutar y _CMD_ para definir parámetros por defecto

<br>

### ¿Qué ocurre al definir un CMD sin definir un ENTRYPOINT?

- Si sólo se especifica un _CMD_, se ejecutará dicho comando usando el _ENTRYPOINT_ por defecto _/bin/sh -c_. No hay _CMD_ por defecto
- Respecto al _entrypoint_ (punto de entrada) y _cmd_ (comando), se puede sobrescribir uno de ellos, ambos o ninguno
- Si se especifican ambos
  - El _ENTRYPOINT_ especifica el ejecutable que usará el contenedor
  - El _CMD_ se corresponde con los parámetros a usar con dicho ejecutable

<br>

### Ejemplo

- Si un Dockerfile contiene
  ```
  FROM ubuntu
  CMD["/bin/date"]
  ```
  se usa el _ENTRYPOINT_ por defecto _/bin/sh -c_, y ejecuta _/bin/date_ sobre dicha entrada.
- El proceso del contenedor se iniciará con la ejecución de _/bin/sh -c /bin/date_
- Al ejecutar esta imagen, el contenedor imprimirá por defecto la fecha actual
  ```
  $ docker build -t cmd-vs-entrypoint .
  $ docker run cmd-vs-entrypoint
  Wed Jul 26 17:23:11 UTC 2023
  ```
- Sin embargo, es posible sobreescribir el comando _CMD_ a usar por defecto desde la misma línea de comandos, ejecutando el comando indicado en el _docker run_
  ```
  $ docker run cmd-vs-entrypoint /bin/hostname
  ae02792e2172
  ```
- Si se usa _ENTRYPOINT_, se usará el ejecutable indicado y _CMD_ permite definir un parámetro por defecto

  ```
  # Dockerfile
  FROM ubuntu
  ENTRYPOINT ["/bin/echo"]
  CMD ["Hello"]

  $ docker build -t cmd-vs-entrypoint .
  $ docker run cmd-vs-entrypoint
  Hello
  ```

- También se puede especificar un valor diferente para _CMD_ al iniciar un contenedor, en lugar del que viene por defecto

  ```
  $ docker run test Hi
  Hi
  ```

- También se puede sobreescribir el valor del _ENTRYPOINT_
  ```
  $ docker run --entrypoint=/bin/hostname cmd-vs-entrypoint
  ae02792e2172
  ```
