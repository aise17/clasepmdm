# Sexta semana

## TEMA 2 INTRODUCCION ANDROID STUDIO

### MARTES - http://www.developandsys.es/elementos-graficos-checkbox-radiobutton-y-otros/ http://www.developandsys.es/elementos-graficos-botones/

**Elemento CheckBox**
***
1. Crear un elemento en el xml
````
<CheckBox
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Ejemplo de Check"
        android:id="@+id/checkboxUno"/>
````
2. Instanciarlo en el .java
````
checkBox = findViewById(R.id.checkboxUno);
````
3. Evaluar su cambio en el estado
````
checkBox.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                Toast.makeText(getApplicationContext(),String.valueOf(isChecked),Toast.LENGTH_SHORT).show();
                checkBox.isChecked();
                checkBox.setSelected(false);

            }
        });
````
**Elemento RadioButton y RadioGroup**
***
Los radiobutton se pueden tratar de forma individual (hay que tener en cuenta que si es pulsado no podrá a ser deseleccinado por parte del usuario)
1. Crear un elemento RadioButton en el xml
````
<RadioButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Radio individual"
        android:id="@+id/radioIndividual"/>
````
2. Instanciarlo en el .java
````
radioInd = findViewById(R.id.radioIndividual);
````
3. Evaluar su pulsación
````
radioInd.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                
            }
        });

// ó

radioGrupoUno.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {

            }
        });
````
Los grupos de radios lo forman varios botones de manera que es imposible que dos botones puedan ser pulsados al mismo tiempo

1. Crear un elemento RadioGroup en el xml junto con los RadioButtons asociados
````
<RadioGroup
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/radioGroup">

        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Radio individual"
            android:id="@+id/radioGrupoUno"/>

        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Radio individual"
            android:id="@+id/radioGrupoDos"/>

    </RadioGroup>
````
2. Instanciarlo en el .java
````
radioGroup = findViewById(R.id.radioGroup);
````
3. Evaluar su pulsación en conjunto
````
radioGroup.setOnCheckedChangeListener(new RadioGroup.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(RadioGroup group, int checkedId) {
                Toast.makeText(getApplicationContext(),findViewById(checkedId).toString(),Toast.LENGTH_SHORT).show();
                group.getCheckedRadioButtonId();
            }
});
````

**Elemento SeekBar**
***
1. Declarar el elemento en el xml
````
<SeekBar
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/seekBar"/>
````
2. Instanciarlo en el .java
````
barra = findViewById(R.id.seekBar);

````

3. Tratar su evento asociado
````
barra.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
            @Override
            public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
                Toast.makeText(getApplicationContext(),findViewById(progress).toString(),Toast.LENGTH_SHORT).show();
                seekBar.getProgress();
                seekBar.setMax(100);
            }

            @Override
            public void onStartTrackingTouch(SeekBar seekBar) {

            }

            @Override
            public void onStopTrackingTouch(SeekBar seekBar) {

            }
        });
````

**Elemento ToogleButton**
***

1. Declarar el elemento en el xml
````
    <ToggleButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/togButton"
        android:textOff="Apagado"
        android:textOn="Encencido"
        android:checked="true"/>
````
2. Instanciarlo en el .java
````
tog = findViewById(R.id.togButton);
````
3. Tratar su evento asociado
````
tog.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                tog.isChecked();
            }
        });
````
**Elemento SwitchButton**
***

Antes de empezar se deben declarar los elementos que se quieren hacer pertenecer al grupo, en este caso botones.
````
    <Button
        android:id="@+id/botonG1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="boton1" />

    <Button
        android:id="@+id/botonG2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="boton2" />

    <Button
        android:id="@+id/botonG3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="boton3" />
````

1. Crear un objeto en el xml
````
<Switch
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:id="@+id/switchButton"/>
````
2. Instanciarlo en el .java
````
aSwitch = findViewById(R.id.switchButton);

````
3. Tratar su evento asociado
````
aSwitch.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                aSwitch.setChecked(true);
                aSwitch.isChecked();
            }
        });
````

### MIÉRCOLES - http://www.developandsys.es/layout/

RelativeLayout y ContraintLayout
***
ContraintLayut es la evolución de relativelayout, utilizando restricciones entre elementos para pode colocarlos. Hay que tener en cuenta que para poder utilizar este tipo de layout hay que tener configuradas las id aunque no se vayan a utilizar en el código java

1. Declarar un ConstraintLayout

````
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

  
</android.support.constraint.ConstraintLayout>
````

2. Crear un elemento inicial situado con respecto a la pantalla mediante las propiedades layout_constraintPosicion

````
<TextView
        android:id="@+id/etiqueta"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="246dp"
        android:layout_marginEnd="162dp"
        android:layout_marginStart="163dp"
        android:layout_marginTop="246dp"
        android:text="Elemento"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
````
2. Crear un elemento y colocarlo con respecto al anterior indicando las restricciones mediante la propiedad layout_constraintPosicion
````
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <TextView
        android:id="@+id/etiqueta"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="246dp"
        android:layout_marginEnd="162dp"
        android:layout_marginStart="163dp"
        android:layout_marginTop="246dp"
        android:text="Elemento"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Etiqeta 2"
        app:layout_constraintTop_toBottomOf="@id/etiqueta" 
        app:layout_constraintStart_toEndOf="@id/etiqueta"/>

</android.support.constraint.ConstraintLayout>
````
**Personaliza el aspecto de un botón**
***
Para poder personalizar el aspecto de un boton se utiliza un xml de tipo selector, donde se le indican las propiedades (pulsado, seleccionado, etc...) y su imagen asociada. Del mismo modo se pueden crear botones con formas (Shapes). Una vez declarado se asigna a la etiqueta src o background (dependiendo del objeto utilizado)
1. En drawable crear un selector
````
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
</selector>
````
2. Asociar estados con imagenes en el fichero creado en items
````
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true" android:drawable="@drawable/up_press"/>
    <item android:state_pressed="false" android:drawable="@drawable/up"/>
</selector>
````
3. Poner el archivo generado como parte del src (o background) del boton 
````
<ImageButton
android:layout_width="0dp"
android:layout_height="match_parent"
android:layout_weight="0.5"
android:src="@drawable/boton_up"
android:background="@null"
android:scaleType="fitCenter"
android:id="@+id/botonUpCartas"
android:alpha="0.1"
/>
````
**Poner una imagen en un elemento ImageView**
***

1. Declarar el elemento en el xml
````
<ImageView
android:layout_width="match_parent"
android:layout_height="match_parent"
android:id="@+id/imagenPrueba"
android:src="@android:drawable/ic_input_add"/>
````
2. Asociarlo al .java
````
imagen = findViewById(R.id.imagenPrueba);
````
3. Utilizar el método setImageResource() donde se indica el id del recurso a utilizar
````
imagen.setImageResource(R.id.nombreImagen);
````

**Generación de arrays en la carpeta res**
***

1. Crear un fichero de tipo values resource file
````
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <integer-array name="numeros">
        <item>4</item>
        <item>8</item>
        <item>1</item>
        <item>2</item>
        <item>4</item>
        <item>5</item>
    </integer-array>

    <array name="imagenes">
        <item>@drawable/c1</item>
        <item>@drawable/c2</item>
        <item>@drawable/c3</item>
        <item>@drawable/c4</item>
        <item>@drawable/c5</item>
        <item>@drawable/c6</item>
        <item>@drawable/c7</item>
        <item>@drawable/c8</item>
        <item>@drawable/c9</item>
        <item>@drawable/c10</item>
        <item>@drawable/c11</item>
        <item>@drawable/c12</item>
        <item>@drawable/c13</item>
    </array>
</resources>
````
2. Introducir el array correspondiente en el xml con el nombre y los elementos que se quieren guardar
````
int[] imagenes = getResources().getIntArray(R.array.numeros);
TypedArray cartas = getResources().obtainTypedArray(R.array.imagenes);
````
3. Acceder al recurso mediante el método getResource().getArray() o getTypedArray() si se han guardado punteros
````
cartas.getResourceId(1,0);
images[0]
````
### JUEVES

### VIERNES 

**Examen**

### PRÁCTICAS A ENTREGAR

#### Primos
***
Realizar una aplicación para el cálculo de numeros primos. Para ello se debe indicar el numero de primos que se quiere calcular. Hay que tener en cuenta que se debe realizar de la forma más eficiente posible

Un número es primo cuando: es divisible sólo por el mismo y por uno, el resto de módulo (divisiones) dan diferente de 0.

![Práctica primos](https://github.com/DevelopSys/clasepmdm/blob/master/practicas/primos.png "Práctica primos")

#### Cartas
***
Realizar una aplicación de cartas Up&Down. Para ello se deberá de indicar si la siguiente carta es mayor o menor. En el caso de aceptar se sumará uno a la puntuación y en el caso de fallar se cerrará la ventana.

Si se ha arrancado la aplicación en modo competición se podrá el record en el campo asignado. En el caso contrario mantendrá el record de la sesión

![Práctica cartas](https://github.com/DevelopSys/clasepmdm/blob/master/practicas/cartas1.png "Práctica cartas") 
 ![Práctica cartas](https://github.com/DevelopSys/clasepmdm/blob/master/practicas/cartas2.png "Práctica cartas")
