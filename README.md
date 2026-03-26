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

El dolor es una experiencia sensorial y emocional compleja asociada con daño tisular real o potencial, que involucra múltiples sistemas fisiológicos, incluyendo el sistema nervioso periférico y central. En el contexto clínico, especialmente durante procedimientos quirúrgicos bajo anestesia general, el paciente pierde la capacidad de comunicar verbalmente su percepción del dolor. Por esta razón, surge la necesidad de desarrollar métodos objetivos de monitoreo que permitan inferir el estado nociceptivo a partir de variables fisiológicas medibles.

Uno de estos métodos es el índice pletismográfico quirúrgico o **Surgical Pleth Index (SPI)**, un parámetro que busca cuantificar el equilibrio entre la nocicepción (respuesta al dolor) y la analgesia. Este índice se calcula a partir de variables derivadas de la señal fotopletismográfica (**PPG**) y de la frecuencia cardíaca, integrando información relacionada con la actividad del sistema nervioso autónomo. El SPI se expresa en una escala de 0 a 100, donde valores bajos indican un estado de menor activación simpática (adecuada analgesia), mientras que valores altos reflejan una mayor respuesta al estrés o al dolor. En entornos clínicos, se considera que un rango aproximado entre 20 y 50 corresponde a un nivel adecuado de analgesia intraoperatoria.

La señal PPG es una técnica óptica no invasiva ampliamente utilizada en instrumentación biomédica. Su funcionamiento se basa en la interacción entre la luz y el tejido biológico: un diodo emisor de luz (LED) ilumina la piel, y un fotodetector mide la cantidad de luz reflejada o transmitida. Debido a que la sangre absorbe la luz en mayor medida que otros tejidos, las variaciones en el volumen sanguíneo durante cada ciclo cardíaco producen cambios periódicos en la señal detectada.

Desde el punto de vista fisiológico, la señal PPG está compuesta por dos componentes principales:

* **Componente DC (corriente continua):** corresponde a la parte constante de la señal y está asociada a estructuras estáticas como la piel, el tejido óseo, la sangre venosa y otros tejidos. Esta componente depende de factores como la posición del sensor, la presión aplicada y las características del tejido.
* **Componente AC (corriente alterna):** representa las variaciones pulsátiles del volumen sanguíneo arterial, sincronizadas con los latidos cardíacos. Esta componente es la más relevante para el análisis fisiológico, ya que contiene información sobre la dinámica cardiovascular.

A partir de la señal PPG es posible extraer múltiples parámetros, como la frecuencia cardíaca, la amplitud del pulso, el tiempo entre latidos (intervalos RR), la variabilidad de la frecuencia cardíaca y la perfusión periférica. La amplitud del pulso, en particular, está directamente relacionada con el volumen de sangre que llega a los tejidos periféricos y, por lo tanto, con el estado de vasodilatación o vasoconstricción.

La base fisiológica del SPI se encuentra en la regulación del **sistema nervioso autónomo (SNA)**, el cual se divide en sistema simpático y parasimpático. El sistema simpático se activa ante situaciones de estrés, dolor o estímulos intensos, generando respuestas como aumento de la frecuencia cardíaca, incremento de la presión arterial y vasoconstricción periférica. Esta vasoconstricción reduce el flujo sanguíneo en las extremidades, lo que se traduce en una disminución de la amplitud de la señal PPG. Por el contrario, cuando predomina el sistema parasimpático, el organismo se encuentra en un estado de reposo y estabilidad, caracterizado por una mayor perfusión periférica y una señal PPG más uniforme.

El cálculo del SPI en sistemas clínicos comerciales combina la información de la amplitud de la onda pletismográfica con la frecuencia cardíaca, utilizando algoritmos propietarios que ponderan estas variables para estimar el nivel de nocicepción. Aunque en esta práctica no se implementó el algoritmo clínico exacto, se realizó una aproximación basada en la relación entre el valor máximo y mínimo de cada pulso, lo que permite estimar la variación relativa de la señal y, por ende, inferir cambios en la perfusión periférica.

Desde el punto de vista del procesamiento de señales, la señal PPG requiere varias etapas para ser analizada correctamente. En primer lugar, es necesario eliminar el offset o componente de línea base, que puede variar debido a factores externos como la presión del sensor o el movimiento del usuario. Posteriormente, se aplican filtros digitales para reducir el ruido de alta frecuencia y las variaciones lentas, mejorando la relación señal-ruido. Una vez acondicionada la señal, se procede a la detección de picos, que corresponde a la identificación de los máximos de cada pulso. Este proceso es crítico, ya que una detección incorrecta afecta directamente el cálculo de los parámetros derivados, como la amplitud del pulso y el SPI.

En esta práctica se implementó un algoritmo de detección basado en el método del “alpinista”, el cual identifica los picos analizando la pendiente de la señal y utilizando un umbral adaptativo que se ajusta dinámicamente en función del comportamiento de la señal. Este tipo de métodos es ampliamente utilizado en el procesamiento de señales biomédicas debido a su capacidad de adaptarse a cambios en la amplitud y el ruido.

Adicionalmente, se empleó el **Cold Pressor Test (CPT)** como herramienta de estimulación fisiológica. Esta prueba consiste en sumergir una extremidad, generalmente la mano, en agua fría durante un periodo determinado, lo que provoca una activación del sistema simpático. Como resultado, se produce vasoconstricción periférica, aumento de la frecuencia cardíaca y cambios en la amplitud de la señal PPG. En teoría, estas variaciones deberían reflejarse en el valor del SPI, permitiendo validar el comportamiento del sistema desarrollado.

Desde la perspectiva de la instrumentación biomédica, el sistema propuesto en la guía incluía varias etapas: un sensor óptico, un circuito de acondicionamiento analógico (amplificación y filtrado), una plataforma de adquisición (Arduino) y un entorno de procesamiento (MATLAB). Sin embargo, en esta práctica se utilizó un módulo integrado que ya incorporaba parte del acondicionamiento de la señal, lo que simplificó el montaje experimental. Aunque esto facilitó la implementación, también limitó el análisis detallado de la etapa analógica y su impacto en la calidad de la señal.

En conjunto, el estudio de la señal PPG y del SPI permite comprender cómo variables fisiológicas complejas pueden ser estimadas a partir de mediciones no invasivas, destacando la importancia de integrar conocimientos de fisiología, electrónica y procesamiento digital de señales en el desarrollo de sistemas biomédicos confiables.

<img width="470" height="500" alt="image" src="https://github.com/user-attachments/assets/146364ab-f2ae-41a8-8349-f4559f6bd1fd" />


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

Inicialmente se verificó la disponibilidad de los elementos necesarios para la práctica. En lugar de construir el circuito de acondicionamiento propuesto en la guía, se decidió trabajar con un módulo sensor de pulso ya ensamblado. Esta decisión permitió reducir el tiempo de montaje y disminuir posibles errores asociados a conexiones incorrectas o desajustes en la etapa analógica, aunque también limitó el análisis detallado del comportamiento electrónico del sistema.

### 2. Conexión del módulo al Arduino

El módulo fue conectado a la placa ESP32 utilizando una entrada analógica para la lectura de la señal, junto con las respectivas conexiones de alimentación y tierra. Posteriormente se verificó el funcionamiento del sistema observando la señal de manera preliminar mediante herramientas como el **Serial Plotter**, confirmando la presencia de una señal pulsátil.

### 3. Adquisición de la señal

Se colocó el dedo de uno de los integrantes sobre el sensor óptico, procurando mantener una posición estable para reducir artefactos por movimiento y variaciones en la presión. La adquisición se realizó durante un tiempo total de **120 segundos**, distribuidos en tres etapas: los primeros **40 segundos en reposo**, los siguientes **40 segundos durante la aplicación del *cold pressor test*** (inmersión en frío), y los últimos **40 segundos nuevamente en reposo**. Durante todo el proceso se verificó que la señal presentara un comportamiento pulsátil coherente con la actividad cardíaca.

### 4. Procesamiento en MATLAB

Se desarrolló un código en MATLAB para capturar la señal proveniente del Arduino durante el intervalo definido. El programa permitió realizar una calibración inicial para centrar la señal, aplicar corrección de línea base y filtrado digital para reducir ruido, e implementar un algoritmo de detección de picos basado en el método del “alpinista” con umbral adaptativo. A partir de la detección de picos, se segmentó la señal pulso a pulso y se calcularon los valores de máximo (Hmax) y mínimo (Hmin) para cada latido, con los cuales se estimó el índice pletismográfico.

Sin embargo, se identificó un error en el algoritmo, ya que la detección de picos no se realizaba correctamente pulso a pulso, lo que generó inconsistencias en la segmentación de los latidos. Como consecuencia, el cálculo del SPI no fue representativo y no reflejó adecuadamente las variaciones fisiológicas esperadas.

### 5. Registro experimental

Durante la adquisición se registraron los datos correspondientes a las tres fases del experimento. Aunque se esperaba observar cambios en el SPI durante el *cold pressor test*, debido a la respuesta del sistema nervioso autónomo, el sistema no evidenció variaciones significativas en el índice, lo cual se asocia directamente con las limitaciones del algoritmo de procesamiento implementado.

### 6. Análisis

Finalmente, los resultados fueron analizados considerando el comportamiento fisiológico esperado y las limitaciones del sistema desarrollado. Se concluyó que, aunque la señal PPG fue correctamente adquirida, la falta de una detección precisa de picos y de un cálculo adecuado del SPI afectó la interpretación de los resultados, evidenciando la importancia de un procesamiento digital robusto en sistemas biomédicos.



## Descripción de lo que se hizo


La práctica consistió en implementar un sistema de medición del índice pletismográfico quirúrgico a partir de una señal PPG adquirida de forma ambulatoria. Aunque la guía de laboratorio planteaba como primera etapa la construcción de un circuito en proto-board para la captura de las variaciones del volumen sanguíneo periférico, en nuestro caso no se construyó dicho circuito. En su lugar, se utilizó un módulo sensor de pulso, el cual ya incluía la etapa básica de detección de la señal.

Después de conectar el módulo al Arduino, se verificó la calidad de la señal observando sus variaciones en tiempo real. Una vez confirmada la presencia de una onda pulsátil adecuada, se procedió a implementar en MATLAB el código encargado de adquirir la señal, procesarla y estimar el SPI. En el código se realizó inicialmente una etapa de calibración para obtener el valor base de la señal, lo que permitió centrarla y eliminar componentes constantes. Posteriormente, la señal fue invertida y sometida a un proceso de corrección de línea base y filtrado digital para reducir ruido y variaciones lentas. 

A continuación, se implementó un algoritmo de detección de picos basado en el método del “alpinista”, el cual identifica los máximos de cada pulso analizando la pendiente de la señal y utilizando un umbral adaptativo que se ajusta dinámicamente según el comportamiento de la señal. Una vez detectados los picos, se segmentó la señal pulso a pulso y se calcularon los valores de máximo (Hmax) y mínimo (Hmin) dentro de cada latido. Con estos valores se estimó el índice pletismográfico mediante la relación entre la amplitud del pulso y su valor máximo.

Adicionalmente, el sistema permitió visualizar en tiempo real la señal cruda, la señal PPG invertida y la señal filtrada, así como mostrar en consola los valores calculados para cada latido. De esta manera, se logró cumplir con el propósito principal de la práctica desde una aproximación funcional, integrando la adquisición, el procesamiento digital y la interpretación básica de la señal, aunque con diferencias respecto al montaje original propuesto en la guía.


### Código implementado con las inconsistencias previamente explicadas:
```
clear
close all
clc

%% CONFIGURACION
puerto = "COM3";
baudrate = 115200;
fs = 100;
Tcal = 5;
windowSec = 6;

ganancia = 1;
alpha = 0.35;
betaBase = 0.01;

Tcaptura = input('Ingrese el tiempo de captura en segundos: ');

%% SERIAL
s = serialport(puerto, baudrate);
configureTerminator(s,"LF");
flush(s);

disp("Iniciando...")
pause(2)

%% CALIBRACION
disp("Calibrando señal...")

Ncal = Tcal * fs;
calData = zeros(Ncal,1);

k = 1;
while k <= Ncal
    if s.NumBytesAvailable > 0
        val = str2double(readline(s));
        if ~isnan(val)
            calData(k) = val;
            k = k + 1;
        end
    end
end

base = mean(calData);
disp("Base lista")

%% BUFFERS
N = windowSec * fs;
t = (-N+1:0)/fs;

rawBuffer      = zeros(N,1);
ppgBuffer      = zeros(N,1);
filtradaBuffer = zeros(N,1);

%% VARIABLES DETECCION
SPKI = 0;
NPKI = 0;
THR1 = 0;

sampleCount = 0;
lastPeak = -1e9;
refractory = round(0.45 * fs);

peakCount = 0;
peakSamples = [];

filtrada = 0;
baselineDyn = 0;

maxSamples = ceil(Tcaptura * fs * 1.5);
senalFiltradaHist = zeros(maxSamples,1);

%% ALPINISTA
subiendo = false;
candPeakVal = -Inf;
candPeakIdx = NaN;
prevProc = 0;

%% FIGURA
figure('Color','k')

subplot(3,1,1)
hRaw = plot(t, rawBuffer,'y','LineWidth',1.4);
title("Señal cruda","Color","w")
grid on
set(gca,'Color','k','XColor','w','YColor','w')

subplot(3,1,2)
hPPG = plot(t, ppgBuffer,'g','LineWidth',1.4);
title("PPG invertida","Color","w")
grid on
set(gca,'Color','k','XColor','w','YColor','w')

subplot(3,1,3)
hFil = plot(t, filtradaBuffer,'c','LineWidth',1.6);
title("Señal filtrada","Color","w")
grid on
set(gca,'Color','k','XColor','w','YColor','w')

sgtitle("Iniciando...","Color","w")

%% TABLA
disp(" ")
disp("==============================================================")
disp(" Latido | Tiempo(s) | Hmax | Hmin | Indice(%)")
disp("==============================================================")

%% LOOP
tInicio = tic;

while toc(tInicio) < Tcaptura

    if s.NumBytesAvailable > 0

        val = str2double(readline(s));

        if ~isnan(val)

            sampleCount = sampleCount + 1;

            if sampleCount > length(senalFiltradaHist)
                senalFiltradaHist = [senalFiltradaHist; zeros(fs*10,1)];
            end

            %% SEÑAL
            senalRaw = val;

            senalBase = senalRaw - base;
            senalPPG = -senalBase * ganancia;

            baselineDyn = (1-betaBase)*baselineDyn + betaBase*senalPPG;
            senalCorregida = senalPPG - baselineDyn;

            filtrada = (1-alpha)*filtrada + alpha*senalCorregida;
            senalFiltradaHist(sampleCount) = filtrada;

            actualProc = filtrada;

            %% BUFFERS
            rawBuffer      = [rawBuffer(2:end); senalRaw];
            ppgBuffer      = [ppgBuffer(2:end); senalPPG];
            filtradaBuffer = [filtradaBuffer(2:end); filtrada];

            %% DETECCION ALPINISTA
            nuevoLatido = false;
            pendiente = actualProc - prevProc;

            if ~subiendo
                if actualProc > THR1 && ...
                   pendiente > 0 && ...
                   (sampleCount - lastPeak) > refractory

                    subiendo = true;
                    candPeakVal = actualProc;
                    candPeakIdx = sampleCount;
                end
            else
                if actualProc >= candPeakVal
                    candPeakVal = actualProc;
                    candPeakIdx = sampleCount;
                end

                if pendiente < 0
                    if (candPeakIdx - lastPeak) > refractory

                        lastPeak = candPeakIdx;
                        peakCount = peakCount + 1;
                        peakSamples = [peakSamples candPeakIdx];
                        nuevoLatido = true;

                        if SPKI == 0
                            SPKI = candPeakVal;
                        else
                            SPKI = 0.2*candPeakVal + 0.8*SPKI;
                        end
                    else
                        if NPKI == 0
                            NPKI = candPeakVal;
                        else
                            NPKI = 0.1*candPeakVal + 0.9*NPKI;
                        end
                    end

                    subiendo = false;
                end
            end

            if ~nuevoLatido && ~subiendo
                if NPKI == 0
                    NPKI = actualProc;
                else
                    NPKI = 0.05*actualProc + 0.95*NPKI;
                end
            end

            prevProc = actualProc;

            %% UMBRAL
            THR1 = NPKI + 0.35*(SPKI - NPKI);

            %% CALCULO PICO A PICO
            if nuevoLatido && length(peakSamples) >= 2

                idx1 = peakSamples(end-1);
                idx2 = peakSamples(end);

                pulso = senalFiltradaHist(idx1:idx2);

                [Hmax, idxMax] = max(pulso);
                zonaValle = pulso(1:idxMax);
                Hmin = min(zonaValle);

                if abs(Hmax) > 1e-9
                    indice = ((Hmax - Hmin)/Hmax)*100;
                else
                    indice = 0;
                end

                indice = max(0,min(100,indice));

                fprintf('%7d | %8.2f | %8.2f | %8.2f | %8.2f\n',...
                    peakCount,...
                    idx2/fs,...
                    Hmax,...
                    Hmin,...
                    indice);
            end

            %% GRAFICAS
            set(hRaw,'YData',rawBuffer)
            set(hPPG,'YData',ppgBuffer)
            set(hFil,'YData',filtradaBuffer)

            %% TITULO
            tiempoRestante = max(Tcaptura - toc(tInicio), 0);
            sgtitle(sprintf("Tiempo restante: %.1f s | Picos: %d",...
                tiempoRestante, peakCount),"Color","w");

            drawnow limitrate
        end
    end
end

disp("==============================================================")
disp("Captura finalizada")

clear 
```


## Análisis de resultados


Los resultados obtenidos mostraron que la señal capturada con el módulo sensor presentaba un comportamiento pulsátil identificable, lo que permitió realizar el procesamiento correspondiente en MATLAB. En condiciones relativamente estables, la amplitud de la señal se mantuvo dentro de un rango consistente, facilitando inicialmente la detección de máximos y mínimos. Sin embargo, durante el análisis se evidenció un error significativo en el algoritmo, ya que la detección de picos no se realizaba correctamente pulso a pulso, lo que generó inconsistencias en la segmentación de los latidos y afectó directamente el cálculo del SPI.

Desde el punto de vista fisiológico, las variaciones observadas en la señal pueden interpretarse como manifestaciones de cambios en la perfusión periférica y en la actividad del sistema nervioso autónomo. No obstante, debido a la falla en la detección adecuada de los picos, estas variaciones no se reflejaron correctamente en el índice calculado. En consecuencia, durante la aplicación del *cold pressor test*, donde se esperaba un aumento de la perfusión periférica y un cambio en el SPI, el sistema no evidenció modificaciones significativas, lo que confirma la influencia crítica del procesamiento de la señal sobre la interpretación fisiológica.

Adicionalmente, factores como el movimiento, la presión del dedo sobre el sensor y el ruido en la señal contribuyeron a introducir variabilidad, la cual, al no ser correctamente manejada por el algoritmo, incrementó el error en la estimación del índice. Esto pone en evidencia que no solo es importante contar con una señal visible y aparentemente estable, sino también garantizar que el procesamiento digital sea robusto y coherente con la dinámica real del pulso.

Al comparar el comportamiento del SPI obtenido experimentalmente con los valores de referencia reportados en contextos clínicos, se debe considerar que el sistema desarrollado no corresponde a un equipo médico certificado ni fue calibrado bajo condiciones controladas. A esto se suma el error en el cálculo del SPI, lo cual limita aún más la validez de los resultados, que deben interpretarse únicamente como una aproximación académica.

Aun así, la práctica permitió evidenciar que el análisis de la señal PPG constituye una base sólida para el desarrollo de sistemas orientados al monitoreo no invasivo de variables fisiológicas complejas. También permitió comprender que el valor del SPI depende no solo de la calidad de la señal adquirida, sino de manera crítica de la correcta detección de picos y del diseño del algoritmo, ya que errores en estas etapas pueden invalidar completamente la interpretación de los resultados.

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

- No se construyó el circuito analógico propuesto en la guía, debido a su dificultad de funcionamiento.
- El uso de un módulo simplificó el sistema, pero redujo el análisis detallado de la etapa de acondicionamiento.
- La señal obtenida presentó sensibilidad al movimiento y a la presión ejercida por el dedo.
- El sistema implementado no cuenta con validación clínica.
- Los valores calculados del SPI son aproximaciones experimentales y no sustituyen equipos médicos especializados.

---

## Moraleja y propuestas de mejora


Una de las principales enseñanzas de esta práctica es que en ingeniería biomédica no basta con obtener una señal o lograr que el sistema funcione de manera básica. También es indispensable comprender a profundidad cada etapa involucrada: desde la adquisición y el acondicionamiento de la señal hasta el procesamiento, la interpretación fisiológica y la validación de los resultados. En nuestro caso, se evidenció un error importante en el algoritmo implementado, ya que la detección de picos no se realizaba correctamente pulso a pulso, lo que generó inconsistencias en la identificación de los latidos y, en consecuencia, en el cálculo del SPI. Esto provocó que los valores obtenidos no fueran representativos y que, durante la aplicación del *cold pressor test*, no se observaran cambios en el índice, cuando fisiológicamente se esperaba una variación.

Aunque el uso del módulo facilitó la ejecución de la práctica y permitió alcanzar resultados funcionales, también dejó claro que la construcción del circuito completo habría aportado una comprensión más sólida sobre el funcionamiento del sistema. Trabajar directamente con la etapa analógica habría permitido analizar con mayor detalle el papel del filtrado, la amplificación, el offset y la relación entre el diseño electrónico y la calidad final de la señal.

Como posibles mejoras se proponen las siguientes:

* Implementar el circuito completo descrito en la guía.
* Aplicar filtros digitales para reducir ruido e interferencias.
* Realizar pruebas con varios sujetos para comparar resultados.
* Estandarizar las condiciones de medición.
* Corregir y robustecer el algoritmo de detección de picos para que funcione correctamente pulso a pulso.
* Ajustar el cálculo del SPI para que refleje adecuadamente los cambios fisiológicos, especialmente en pruebas como el *cold pressor test*.
* Comparar los resultados con instrumentos biomédicos comerciales.

La moraleja principal es que un sistema biomédico debe ser no solo funcional, sino también comprensible, reproducible, confiable y validable, ya que pequeños errores en el procesamiento pueden generar resultados incorrectos incluso cuando la señal parece adecuada.



## Conclusión

La práctica permitió comprender de manera integral el proceso de adquisición y análisis de la señal fotopletismográfica para estimar el índice pletismográfico quirúrgico, evidenciando que, aunque se empleó un módulo en lugar de un circuito diseñado desde cero, fue posible obtener resultados funcionales y analizar la variación de la perfusión periférica. Sin embargo, durante el desarrollo se presentó un error importante en el código, ya que la detección de picos no se realizaba correctamente pulso a pulso, lo que generó inconsistencias en el cálculo y provocó que los valores de SPI no fueran representativos. Como consecuencia, al aplicar el cold pressor test no se observaron cambios en el índice, lo que evidencia limitaciones en el procesamiento de la señal. A pesar de ello, la experiencia permitió identificar la importancia de una correcta detección de picos y de un adecuado procesamiento digital, fortaleciendo la comprensión de la relación entre señales fisiológicas y su interpretación en contextos biomédicos, así como la necesidad de validar y mejorar continuamente los sistemas desarrollados.


---

## Bibliografía


1.	Sciencedirect.com. [En línea]. Disponible en: https://www.sciencedirect.com/topics/medicine-and-dentistry/cold-pressor-test. [Consultado: 26-mar-2026].

2.	Wikipedia contributors, “Serial Peripheral Interface”, Wikipedia, The Free Encyclopedia, 13-mar-2026. [En línea]. Disponible en: https://en.wikipedia.org/w/index.php?title=Serial_Peripheral_Interface&oldid=1343364517.

3.	S. Guerrero-Zúñiga et al., “No title”, Org.mx, 2016. [En línea]. Disponible en: https://www.scielo.org.mx/scielo.php?pid=S0028-37462016000400296&script=sci_abstract&tlng=pt. [Consultado: 26-mar-2026].

4. M. Huiku, K. Uutela, M. van Gils, I. Korhonen, M. Kymäläinen, P. Meriläinen, M. Paloheimo, M. Rantanen, P. Takala, H. Viertiö-Oja y A. Yli-Hankala, “Assessment of surgical stress during general anaesthesia,” *British Journal of Anaesthesia*, vol. 98, no. 4, pp. 447–455, 2007.

5. S. Funcke, S. Sauerlaender, H. O. Pinnschmidt, B. Saugel, K. Bremer, D. A. Reuter, R. Nitzschke y otros, “Validation of innovative techniques for monitoring nociception during general anesthesia: a clinical study using tetanic and intracutaneous electrical stimulation,” *Anesthesiology*, vol. 127, no. 2, pp. 272–283, 2017.

---

## Evidencias

### Señal capturada

<img width="1146" height="542" alt="image" src="https://github.com/user-attachments/assets/fe0ebd48-eabc-4b37-b59b-e40d72b8676d" />

<img width="627" height="505" alt="image" src="https://github.com/user-attachments/assets/3f817391-c0e8-42ee-9856-1e234d414ea7" />


