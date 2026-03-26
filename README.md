# C-lculo-ambulatorio-del-ndice-pletismogr-fico-quir-rgico-SPI-
Sara Damaris Vasquez Cardenas y Paula Andrea Vega


## Introducción

En el ámbito de la medicina moderna, especialmente en procedimientos quirúrgicos bajo anestesia general, la evaluación objetiva del dolor representa un desafío significativo, dado que el paciente no puede expresar de manera consciente su percepción nociceptiva. Esta limitación ha impulsado el desarrollo de herramientas biomédicas capaces de estimar el nivel de dolor de forma indirecta, a partir de variables fisiológicas medibles.

Uno de los métodos más relevantes en este contexto es el índice pletismográfico quirúrgico (SPI), el cual permite evaluar el balance entre nocicepción y analgesia mediante el análisis de la señal fotopletismográfica (PPG). Esta señal refleja las variaciones del volumen sanguíneo periférico, las cuales están estrechamente relacionadas con la actividad del sistema nervioso autónomo. De esta manera, el SPI se convierte en una herramienta útil para monitorear la respuesta del organismo frente a estímulos dolorosos, contribuyendo a una mejor administración de anestesia y analgesia durante procedimientos clínicos.

En esta práctica de laboratorio se abordó el desarrollo de un sistema capaz de capturar la señal PPG y calcular el índice SPI en condiciones ambulatorias. Aunque la guía planteaba la construcción de un circuito electrónico completo para la adquisición de la señal, se optó por el uso de un módulo sensor integrado, lo cual permitió simplificar el montaje y enfocar el trabajo en la adquisición y procesamiento de la señal.

El desarrollo de esta práctica permitió integrar conocimientos de instrumentación biomédica, fisiología y procesamiento de señales, así como comprender la importancia de los sistemas no invasivos en el monitoreo clínico. Además, se analizaron las limitaciones del sistema implementado y su relación con los dispositivos utilizados en entornos médicos reales.

---

## Objetivo general

Desarrollar un sistema de medición continua del índice pletismográfico quirúrgico (SPI) en condiciones ambulatorias.

## Objetivos específicos

- Reconocer las características fundamentales de la onda de pulso a partir de las cuales se obtiene el SPI.
- Implementar un sistema capaz de calcular el SPI en tiempo real.
- Analizar la respuesta fisiológica observada mediante la señal PPG.
- Comparar los resultados obtenidos con el comportamiento esperado del SPI en aplicaciones clínicas.

---

## Marco teórico

El dolor es una experiencia sensorial y emocional compleja asociada con daño tisular real o potencial. En procedimientos quirúrgicos bajo anestesia general, el paciente no puede comunicar verbalmente si está experimentando un estímulo nociceptivo, por lo que se requiere el uso de herramientas de monitoreo fisiológico que permitan estimar objetivamente dicho estado.

El índice pletismográfico quirúrgico o **SPI** es una de estas herramientas. Se trata de un parámetro que se calcula a partir de variables derivadas de la señal fotopletismográfica (**PPG**), una señal óptica no invasiva que representa las variaciones del volumen sanguíneo periférico producidas por cada latido cardíaco.

La fotopletismografía funciona mediante la emisión de luz hacia el tejido y la detección de la cantidad de luz reflejada o transmitida. Como el volumen de sangre cambia cíclicamente con cada pulso, también cambia la cantidad de luz absorbida, generando una señal que puede analizarse en el tiempo. Esta señal presenta dos componentes principales:

- **Componente DC:** asociada al volumen constante de tejidos, sangre venosa y estructuras estáticas.
- **Componente AC:** asociada a las variaciones pulsátiles del flujo sanguíneo arterial.

A partir de la señal PPG es posible obtener información sobre la frecuencia cardíaca, la amplitud del pulso, la perfusión periférica y otras variables relacionadas con la actividad cardiovascular.

El SPI se relaciona con el equilibrio entre nocicepción y analgesia, y toma valores entre 0 y 100. En términos generales, valores bajos indican menor activación simpática y valores altos indican una mayor respuesta fisiológica asociada al estrés o al dolor. En el contexto quirúrgico, se considera que un rango aproximado entre 20 y 50 corresponde a una analgesia intraoperatoria adecuada.

La base fisiológica del SPI se encuentra en la actividad del **sistema nervioso autónomo**. Cuando un individuo está sometido a dolor, estrés o estímulos intensos, el sistema simpático se activa, generando respuestas como aumento de la frecuencia cardíaca, vasoconstricción periférica y cambios en la amplitud de la onda de pulso. En cambio, cuando predomina el sistema parasimpático, el organismo se encuentra en un estado de mayor estabilidad fisiológica.

En esta práctica también resulta importante mencionar el **Cold Pressor Test (CPT)**, una maniobra que consiste en exponer una extremidad a agua fría durante un periodo corto. Este procedimiento induce una respuesta simpática medible, lo que permite observar cambios fisiológicos similares a los producidos ante un estímulo doloroso. Aunque esta prueba se plantea en la guía como método de validación, su utilidad radica en provocar modificaciones en la frecuencia cardíaca y en la perfusión periférica, afectando así la señal PPG y el valor estimado del SPI.

Desde el punto de vista de la instrumentación biomédica, el sistema propuesto en la guía incluía un sensor óptico, una etapa de acondicionamiento analógico con amplificación y filtrado, una tarjeta Arduino para adquisición y MATLAB para el procesamiento de los datos. Sin embargo, en el desarrollo real de esta práctica se utilizó un **módulo integrado**, lo que permitió simplificar el proceso experimental y centrar la atención en la captura de la señal y el cálculo del índice.

---

## Materiales utilizados

- Computador 
- MATLAB
- ESP32
- Módulo sensor de pulso max30102
- Cables de conexión
- Software de adquisición y visualización de datos

> **Nota:** Aunque la guía proponía construir un circuito completo de adquisición, en esta práctica se utilizó un módulo ya integrado en lugar del circuito implementado en proto-board.

---

## Metodología

### 1. Preparación del sistema

Inicialmente se verificó la disponibilidad de los elementos necesarios para la práctica. En lugar de construir el circuito de acondicionamiento propuesto en la guía, se decidió trabajar con un módulo sensor de pulso ya ensamblado. Esta decisión permitió reducir el tiempo de montaje y disminuir posibles errores asociados a conexiones incorrectas o desajustes en la etapa analógica.

### 2. Conexión del módulo al Arduino

El módulo fue conectado a la placa Arduino utilizando una entrada analógica para la lectura de la señal. También se realizaron las conexiones de alimentación y tierra correspondientes. Posteriormente se verificó que la señal pudiera observarse de manera preliminar mediante herramientas como el **Serial Plotter**.

### 3. Adquisición de la señal

Se colocó el dedo de uno de los integrantes sobre el sensor óptico, procurando mantener una posición estable para reducir artefactos por movimiento. Se observó la señal obtenida y se verificó que presentara un comportamiento pulsátil coherente con la actividad cardíaca.

### 4. Procesamiento en MATLAB

Se desarrolló un código en MATLAB para capturar la señal proveniente del Arduino durante un intervalo determinado. El programa permitió:

- Leer la señal en tiempo real.
- Detectar máximos y mínimos asociados a cada pulso.
- Estimar parámetros de interés a partir de la señal capturada.
- Calcular el SPI para cada pulsación o intervalo definido.
- Visualizar la evolución temporal del índice.

### 5. Registro experimental

La captura se realizó durante un tiempo finito establecido por el grupo. Durante este intervalo se analizaron las características de la señal en estado de reposo y, en caso de realizarse una maniobra de estimulación fisiológica, se comparó el comportamiento del SPI antes, durante y después del estímulo.

### 6. Análisis

Finalmente, se interpretaron los resultados obtenidos teniendo en cuenta el comportamiento fisiológico esperado del sistema nervioso autónomo y las limitaciones del montaje utilizado.

---

## Descripción de lo que se hizo

La práctica consistió en implementar un sistema de medición del índice pletismográfico quirúrgico a partir de una señal PPG adquirida de forma ambulatoria. Aunque la guía de laboratorio planteaba como primera etapa la construcción de un circuito en proto-board para la captura de las variaciones del volumen sanguíneo periférico, en nuestro caso no se construyó dicho circuito. En su lugar, se utilizó un **módulo sensor de pulso**, el cual ya incluía la etapa básica de detección de la señal.

Después de conectar el módulo al Arduino, se verificó la calidad de la señal observando sus variaciones en tiempo real. Una vez confirmada la presencia de una onda pulsátil adecuada, se procedió a implementar en MATLAB el código encargado de adquirir la señal, procesarla y estimar el SPI.

La señal obtenida permitió identificar pulsos sucesivos, calcular variables relacionadas con la frecuencia y la amplitud, y representar gráficamente la evolución del índice durante el periodo de medición. De esta manera, se logró cumplir con el propósito principal de la práctica desde una aproximación funcional, aunque con diferencias respecto al montaje original propuesto en la guía.

---

## Análisis de resultados

Los resultados obtenidos mostraron que la señal capturada con el módulo sensor presentaba un comportamiento pulsátil identificable, lo que permitió realizar el procesamiento correspondiente en MATLAB. En condiciones relativamente estables, la amplitud de la señal se mantuvo dentro de un rango consistente, facilitando la detección de máximos y mínimos.

Desde el punto de vista fisiológico, las variaciones observadas en la señal pueden interpretarse como manifestaciones de cambios en la perfusión periférica y en la actividad del sistema nervioso autónomo. Cuando el organismo se encuentra en reposo, la señal suele ser más uniforme y con menor interferencia, mientras que ante movimiento, tensión muscular, presión excesiva del dedo o estímulos externos, se presentan alteraciones que afectan tanto la amplitud como la periodicidad de la onda.

Al comparar el comportamiento del SPI obtenido experimentalmente con los valores de referencia reportados en contextos clínicos, se debe tener en cuenta que el sistema desarrollado no corresponde a un equipo médico certificado ni fue calibrado bajo condiciones hospitalarias. Por esta razón, los valores calculados deben interpretarse más como una aproximación académica que como una medición clínica exacta.

Aun así, la práctica permitió evidenciar que el análisis de la señal PPG constituye una base sólida para el desarrollo de sistemas orientados al monitoreo no invasivo de variables fisiológicas complejas. También permitió comprender que el valor del SPI depende no solo de la calidad del algoritmo implementado, sino también de la calidad de la señal adquirida y de la robustez del sistema de instrumentación.

---

## Respuestas a las preguntas de discusión

### Pregunta 1: ¿Cómo se relacionan las variaciones del volumen sanguíneo periférico con el balance autonómico?

Las variaciones del volumen sanguíneo periférico se encuentran estrechamente relacionadas con la actividad del sistema nervioso autónomo, en especial con el equilibrio entre la rama simpática y la parasimpática. Cuando predomina la actividad simpática, como ocurre en situaciones de dolor, estrés o frío, se produce vasoconstricción periférica. Esta respuesta disminuye el flujo sanguíneo en ciertas regiones del cuerpo y altera la amplitud de la señal PPG. Por el contrario, cuando la actividad parasimpática es predominante, el organismo tiende a un estado de reposo más estable, favoreciendo una perfusión periférica más uniforme.

Por ello, las modificaciones en la señal PPG permiten inferir indirectamente cambios en el balance autonómico. Una disminución de la amplitud o una alteración en la forma del pulso puede asociarse con una respuesta simpática aumentada, mientras que una señal más regular puede relacionarse con mayor estabilidad fisiológica.

### Pregunta 2: ¿Cómo se compara el SPI con otros índices comúnmente empleados en cirugía, como el índice nocicepción-analgesia (ANI) y el índice de perfusión?

El SPI, el ANI y el índice de perfusión son herramientas utilizadas para analizar la respuesta fisiológica del paciente, pero no evalúan exactamente lo mismo.

El **SPI** se enfoca en estimar el balance entre nocicepción y analgesia a partir de variables derivadas de la señal pletismográfica y del comportamiento cardiovascular. Es un índice diseñado específicamente para apoyar el monitoreo intraoperatorio.

El **ANI** se basa principalmente en la variabilidad de la frecuencia cardíaca y está más relacionado con la actividad parasimpática. Por esta razón, puede ofrecer información valiosa sobre el estado autonómico del paciente, aunque desde una perspectiva diferente a la del SPI.

El **índice de perfusión**, por su parte, mide la intensidad del pulso periférico y la calidad de la perfusión en el sitio de medición. Aunque puede verse afectado por el dolor o por la actividad simpática, no fue diseñado específicamente como un índice de nocicepción.

En comparación, el SPI ofrece una aproximación más orientada a la valoración del equilibrio nocicepción-analgesia, mientras que el ANI y el índice de perfusión brindan información complementaria sobre la regulación autonómica y el estado circulatorio periférico.

---

## Limitaciones del trabajo

Durante el desarrollo de la práctica se identificaron varias limitaciones importantes:

- No se construyó el circuito analógico propuesto en la guía.
- El uso de un módulo simplificó el sistema, pero redujo el análisis detallado de la etapa de acondicionamiento.
- La señal obtenida presentó sensibilidad al movimiento y a la presión ejercida por el dedo.
- El sistema implementado no cuenta con validación clínica.
- Los valores calculados del SPI son aproximaciones experimentales y no sustituyen equipos médicos especializados.

---

## Moraleja y propuestas de mejora

Una de las principales enseñanzas de esta práctica es que en ingeniería biomédica no basta con obtener una señal o lograr que el sistema funcione de manera básica. También es indispensable comprender a profundidad cada etapa involucrada: desde la adquisición y el acondicionamiento de la señal hasta el procesamiento, la interpretación fisiológica y la validación de los resultados.

Aunque el uso del módulo facilitó la ejecución de la práctica y permitió alcanzar resultados funcionales, también dejó claro que la construcción del circuito completo habría aportado una comprensión más sólida sobre el funcionamiento del sistema. Trabajar directamente con la etapa analógica habría permitido analizar con mayor detalle el papel del filtrado, la amplificación, el offset y la relación entre el diseño electrónico y la calidad final de la señal.

Como posibles mejoras se proponen las siguientes:

- Implementar el circuito completo descrito en la guía.
- Aplicar filtros digitales para reducir ruido e interferencias.
- Realizar pruebas con varios sujetos para comparar resultados.
- Estandarizar las condiciones de medición.
- Mejorar el algoritmo de detección de picos y cálculo del SPI.
- Comparar los resultados con instrumentos biomédicos comerciales.

La moraleja principal es que un sistema biomédico debe ser no solo funcional, sino también comprensible, reproducible, confiable y validable.

---

## Conclusión

La práctica permitió desarrollar un sistema de adquisición y procesamiento de señal fotopletismográfica con el fin de estimar el índice pletismográfico quirúrgico en condiciones ambulatorias. A partir de la señal obtenida con un módulo sensor de pulso y su posterior procesamiento en MATLAB, fue posible identificar pulsaciones, analizar variaciones del volumen sanguíneo periférico y calcular una aproximación del SPI.

Aunque el procedimiento ejecutado difirió del planteamiento original de la guía, ya que no se construyó el circuito electrónico propuesto sino que se utilizó un módulo integrado, los resultados obtenidos permitieron cumplir parcialmente con los objetivos académicos de la práctica. Además, se comprendió la relación entre la señal PPG, la regulación autonómica y la estimación indirecta de la respuesta fisiológica al dolor.

De igual manera, la experiencia evidenció que la calidad del sistema depende tanto del hardware utilizado como del algoritmo de procesamiento implementado. También permitió reconocer las limitaciones de trabajar con montajes simplificados y la importancia de validar experimentalmente los resultados antes de extrapolarlos a contextos clínicos.

En conclusión, esta práctica fue valiosa para integrar conocimientos de fisiología, electrónica e instrumentación biomédica, y para reflexionar sobre la importancia de diseñar sistemas no invasivos capaces de aportar información útil en el monitoreo de pacientes.

---

## Bibliografía

1. J. L. Apfelbaum, C. Chen, S. S. Mehta y T. J. Gan, “Postoperative pain experience: results from a national survey suggest postoperative pain continues to be undermanaged,” *Anesthesia & Analgesia*, vol. 97, no. 2, pp. 534–540, 2003.

2. T. Ledowski, “Objective monitoring of nociception: a review of current commercial solutions,” *British Journal of Anaesthesia*, vol. 123, no. 2, pp. e312–e321, 2019.

3. V. Bonhomme, K. Uutela, G. Hans, I. Maquoi, J. D. Born y J. F. Brichant, “Comparison of the Surgical Pleth Index™ with haemodynamic variables to assess nociception-anti-nociception balance during general anaesthesia,” *British Journal of Anaesthesia*, vol. 106, no. 1, pp. 101–111, 2011.

4. M. Huiku, K. Uutela, M. van Gils, I. Korhonen, M. Kymäläinen, P. Meriläinen, M. Paloheimo, M. Rantanen, P. Takala, H. Viertiö-Oja y A. Yli-Hankala, “Assessment of surgical stress during general anaesthesia,” *British Journal of Anaesthesia*, vol. 98, no. 4, pp. 447–455, 2007.

5. S. Funcke, S. Sauerlaender, H. O. Pinnschmidt, B. Saugel, K. Bremer, D. A. Reuter, R. Nitzschke y otros, “Validation of innovative techniques for monitoring nociception during general anesthesia: a clinical study using tetanic and intracutaneous electrical stimulation,” *Anesthesiology*, vol. 127, no. 2, pp. 272–283, 2017.

---

## Evidencias

### Señal capturada
_Aquí puedes insertar una imagen de la señal obtenida._

```bash
![Señal PPG](ruta/de/la/imagen.png)
