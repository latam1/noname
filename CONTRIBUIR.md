# Contribuyendo
Gracias por considerar contribuir. Tus contribuciones ayudan a mejorar y expandir esta estudio para el desarrollo en torno a Bitcoin y economias en via de desarrollo.

## Cómo contribuir
### 1. Informar sobre un problema

Si encuentras algún error o tienes algun comentario , puedes crear un incidente en la página [GitHub Issues](https://github.com/latam1/noname/issues).

### 2. Solicitudes especificas 

Si tiene una idea para una nueva o mejora, crea un incidente para discutirla antes de enviar una solicitud de incorporación de cambios. Esto ayuda a garantizar la alineación con los objetivos del proyecto y su mantenibilidad.

### 3. para Contribucir de manera formal

#### Paso 1: Crea una copia del repositorio localmente 

1. Bifurca el repositorio en GitHub.
2. Clona tu bifurcación en tu equipo local:
```sh
git clone https://github.com/your-username/python-bitcoin-utils.git
cd python-bitcoin-utils
```
3. Agrega el repositorio original para mantener tu bifurcación actualizada:
```sh
git remote add upstream https://github.com/karask/python-bitcoin-utils.git
```

#### Paso 2: Crea una rama de funciones

Crea una nueva rama para tus cambios:
```sh
git checkout -b feature-name
```

#### Paso 3: Realiza cambios y prueba

- Sigue el estilo de codificación del proyecto. - Asegúrate de que tu código esté bien documentado e incluya mensajes de confirmación relevantes.
- Instala el paquete en modo de desarrollo antes de ejecutar las pruebas:
```sh
pip install -e .
```
Esto crea una instalación editable que enlaza con tu código local, lo cual es necesario para que las pruebas detecten e importen correctamente los módulos.
- Ejecuta las pruebas antes de enviar una solicitud de extracción:
```sh
pytest tests/
```
Asegúrate de que todas las pruebas sean correctas y que los cambios no generen regresiones.

#### Paso 4: Enviar una solicitud de extracción

1. Sube los cambios a la rama de tu bifurcación:
```sh
git push origin feature-name
```
2. Abre una solicitud de extracción desde la rama de tu bifurcación a la rama `master` del repositorio original.
3. Proporciona una descripción detallada de los cambios.
4. Atiende cualquier cambio solicitado por los mantenedores.

### 4. Directrices de estilo de código

- Sigue la norma PEP 8 para el estilo de código Python. - Use nombres de variables y funciones con significado.
- Mantenga la documentación del código clara y concisa.
- Use 4 espacios para la sangría, no tabulaciones.
- Use comillas dobles triples (""") para las cadenas de documentación.
- Incluya sugerencias de tipo para los parámetros de función y los valores de retorno.
- La longitud máxima de línea debe ser de 88 caracteres.
- Use nombres de variables descriptivos que expliquen su propósito.
- No cambie el control de versiones en __init__; el mantenedor lo haría periódicamente.
