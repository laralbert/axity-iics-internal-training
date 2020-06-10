# Mappings

En esta lección aprenderemos a generar mapeo de datos y transformaciones de Informatica:

- Mapeo Directo
- Expression
- Filtros
- Router
- Agrupación

1. Ingresamos a [IICS](https://dm-us.informaticacloud.com) y seleccionamos **Data Integration**.

![Mapping](images/img_map_01.jpg)

2. En la pantalla de inicio podemos visualizar una estadística de la cantidad de objetos tenemos. Dar clic en **Explorar**.

![Mapping](images/img_map_02.jpg)

3. Ingresar en el proyecto **_pro_cap_iics** y posteriormente dar clic en **New Folder**.

![Mapping](images/img_map_03.jpg)

4. En la ventana que se desplegó, ingresar las iniciales del participante y una breve descripción.

![Mapping](images/img_map_04.jpg)

## Mapeo Directo

1. Después de crear la carpeta, en el panel izquierdo dar clic en el botón **Nuevo**. Seleccionamos **Mappings**->**Mapping** y dar clic en **Create**.

![Mapping](images/img_map_05.jpg)

2. Nombramos nuestro mapping **M_Practica** y agregamos una breve descripción.

![Mapping](images/img_map_06.jpg)

3. Seleccionar el objeto **Source** y después seleccionar la sección **Source**. Realizar la siguiente configuración:

	- Connection: **_conn_File_input**
	- Source_Type: **Single Objet**
	- Object: **netflix_titles.csv**

![Mapping](images/img_map_07.jpg)

> Al dar clic en **Select** se nos desplegarán los archivos asociados a la conexión. Seleccionamos **netflix_titles.csv** y dar clic en **OK**.

![Mapping](images/img_map_08.jpg)

4. Para validar que el archivo se puede visualizar correctamente, elegir la opción **Preview Data**, en caso de que marque algún error seleccionamos **Formatting Options** y elegir manualmente el tipo de formato del archivo.

5. Seleccionamos el objeto **Target** y después seleccionar la sección **Target**. Realizar la siguiente configuración:

	- Connection: **_conn_File_output**
	- Source_Type: **Single Objet**
	- Object: **Salida_Netflix.csv**

![Mapping](images/img_map_09.jpg)

6. Al seleccionar el **Objeto** debemos elegir **Create New at Runtime** e ingresar el nombre del archivo de salida **Salida_Netflix.csv**. En caso de ser necesario seleccionar **Formatting Options**.

![Mapping](images/img_map_10.jpg)

7. En este menú podemos determinar el tipo de formato para la salida de nuestro archivo, por default se genera con las siguientes características:

![Mapping](images/img_map_11.jpg)

8. Al finalizar la configuración de **Target**, guardar los cambios y revisar que el mapping esté en estatus **Valid**. Finalmente ejecutamos el mapping.

![Mapping](images/img_map_12.jpg)

9. Al seleccionar **Run**, se nos desplegará una ventana donde elegiremos el Agente Seguro con el que se va a ejecutar el mapping, seleccionar **vm-training** y dar clic en **Run**.

![Mapping](images/img_map_13.jpg)

10. Abrimos una nueva página de IICS y seleccionamos **Monitor**.

![Mapping](images/img_map_14.jpg)

11. En el menú de Monitor veremos los Jobs que se encuentran corriendo **Running Jobs**, en caso de no visualizar nuestro mapping seleccionamos **All Jobs** y verificamos el estatus de nuestro Job, en caso de requerir más detalle dar clic en el nombre de nuestro mapping.

![Mapping](images/img_map_15.jpg)

12. En el detalle del monitor podemos visualizar el número de registros leídos y procesados, en caso de alguna falla se nos mostrará el error y los registros rechazados, para más detalle podemos dar clic en **Download Session Log**

![Mapping](images/img_map_16.jpg)

## Expression

1. Entrar a la carpeta de trabajo y seleccionar el mapping que creamos previamente **M_Practica**, dar clic derecho y seleccionar **Copy To**, elegimos nuestra carpeta de trabajo y cambiamos el nombre del mapping por **M_Practica_Exp**.

![Mapping](images/img_me_01.png)

2. En **Source** seleccionamos **Fields** y modificamos la metadata, para cambiar el tipo de dato del campo **release_year** a **integer** de **10**.

![Mapping](images/img_me_02.png)

3. Desde la paleta de transformaciones agregamos al mapping un **Expression** y lo enlazamos desde el **Source**.

![Mapping](images/img_me_03.png)

4. En las propiedades del **Expression** seleccionamos **Expression** y después en **+** para agregar un nuevo puerto y configurarlo de la siguiente manera:

![Mapping](images/img_me_04.png)

5. En el nuevo puerto dar clic **Configure...**.

![Mapping](images/img_me_05.png)

6. Configurar el nuevo puerto de la siguiente manera.

![Mapping](images/img_me_06.png)

7. Creamos un nuevo puerto que se llama **Categoria_out** de tipo **String** de **10** y agregamos el siguiente código:

```
IIF (release_year < 2000, 'Clasicas', 'Actuales')
```

![Mapping](images/img_me_07.png)

> Con la opción **Build-in Function** se pueden ver todas las funciones disponibles y su sintaxis.

8. Conectar el **Expression** al **Target**. Seleccionar el **Target** y seleccionar **Incoming Fields**. Los nuevos puertos se visualizarán en la columna **Origin** con el nombre del **Expression**.

![Mapping](images/img_me_08.png)

> En la sección de **Target** cambiar el nombre del archivo de salida **Categoria_Exp_[iniciales].csv**

9. **Guardar** los cambios, revisar que el mapping sea **Válido** y **Ejecutar**.

10. Validar en el monitor que el proceso se ejecutó correctamente y después revisar el archivo de salida para validar que se encuentran los dos nuevos campos.

![Mapping](images/img_me_09.png)

## Filter

1. Duplicar el mapa **M_Practica_Exp** y renombrarlo como **M_Practica_Fil**.

2. Agregar en el mapping un **Filter** y conectarlo entre el **Expression** y el **Target**.

![Mapping](images/img_mf_01.png)

3. En las propiedades del Filtro, seleccionar **Filter** y dar clic en el símbolo **+**. En la configuración utilizaremos el campo **Release_year** donde el operador sea **>** de **1990**.

![Mapping](images/img_mf_02.png)

> **Nota:** El campo que se ocupará en la condición debe tener un tipo de dato válido, en este ejemplo es *Integer*.

4. Conectamos el **Filter** al **Target** y configuramos la salida del archivo como **Categoria_Fil_Iniciales.csv**.

5. **Guardar** los cambios, revisar que el mapping sea **Válido** y **Ejecutar**.

6. En el monitor podemos visualizar que el total de registros de entrada es diferente a los de salida, ya que al agregar el filtro únicamente pasan aquellos registros que cumplen con la regla.

![Mapping](images/img_mf_03.png)

## Router

Esta transformación es muy parecida al filtro, pero nos permite generar una o más salidas por medio grupos y cada uno con condiciones diferentes.

1. Duplicar el mapping **M_Practica_Exp** y renombrarlo como **M_Practica_Rtr**.

2. Agregar en el mapping un **Router** entre el **Expression** y el **Target**.

![Mapping](images/img_mrtr_01.png)

3. En las propiedades del Router, seleccionar **Output Groups**, dar clic en el simbol **+**, renombramos el grupo como **N_2000** y damos clic en **Configure...**

![Mapping](images/img_mrtr_02.png)

4. En esta pantalla damos clic en **+** y agregamos una condición donde el valor del campo **release_year** sea **igual a 2000**.

![Mapping](images/img_mrtr_03.png)

5. Generamos 2 grupos más para los años 2010 y 2019, quedando de la siguiente manera:

![Mapping](images/img_mrtr_04.png)

6. Agregamos 3 **Target's** al mapping con los siguientes nombres:

	- T_Salida_2000
	- T_Salida_2010
	- T_Salida_2019

7. Enlazar el **Router** con los **Target's**, para realizar esto damos clic en el símbolo **+** para que se desplieguen los grupos y poder enlazarlos con el **Target** que corresponde.

![Mapping](images/img_mrtr_05.png)

> **Nota:** El grupo **DEFAULT1** nos devuelve los registros que no cumplen con ninguna condición, es opcional enlazarlo con algún **Target**.

8. Configuramos las salidas de los **Target's** dejando como salida los siguientes archivos:

	- Categoria_2000_iniciales.csv
	- Categoria_2010_iniciales.csv
	- Categoria_2019_iniciales.csv

9. **Guardar** los cambios, revisar que el mapping sea **Válido** y **Ejecutar**.

10. En el Monitor podemos validar que se cargue información en cada **Target** si estos cumplieron con la condición, como se muestra en la siguiente imagen:

![Mapping](images/img_mrtr_06.png)

## Aggregator

1. Duplicar el mapping **M_Practica_Exp** y renombrarlo como **M_Practica_Agg**

2. Agregar en el mapping un **Aggregator** entre el **Expression** y el **Target**.

![Mapping](images/img_magg_01.png)

3. En las propiedades del **Aggregator** seleccionar **Incoming Fields**, seleccionar la regla actual y configurarla de la siguiente manera:

![Mapping](images/img_magg_02.png)

4. De la columna **Details** dar clic en **3 fields**.

5. Seleccionamos en los campos que vamos a utilizar, en este caso serán: **Categoria_out**, **release_year** y **type**.

![Mapping](images/img_magg_03.png)

6. Seleccionar la sección **Group by** y dar clic en el símbolo **+** para agregar los campos por los que se agruparán los datos **(type y Categoria_out)**.

![Mapping](images/img_magg_04.png)

7. Seleccionar la sección **Aggregate** y dar clic en el símbolo **+** para agregar dos campos con la siguiente configuración:

![Mapping](images/img_magg_05.png)

![Mapping](images/img_magg_06.png)

![Mapping](images/img_magg_07.png)

8. En la columna **Expresión** dar clic en cada opción para configurar las reglas de agregación como sigue:

	- **Conteo ->** `count(*)`
	- **Anio_Max ->** `max(release_year)`

![Mapping](images/img_magg_08.png)

![Mapping](images/img_magg_09.png)

9. Enlazamos el **Aggregator** al **Target** y configuramos la salida del archivo como **Categoria_Agg_[Iniciales].csv**

10. **Guardar** los cambios, revisar que el mapping sea **Válido** y **Ejecutar**.

11. En el monitor podemos visualizar la cantidad de registros que arroja el mapping después de la agrupación.

![Mapping](images/img_magg_10.png)

12. Los datos se visualizarán de la siguiente forma

![Mapping](images/img_magg_11.png)
