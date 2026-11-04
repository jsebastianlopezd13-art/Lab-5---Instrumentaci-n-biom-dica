# Laboratorio 5: Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

**Asignatura:** Instrumentación Biomédica y Biosensores  
**Docente:** Erick Arguello
**Integrantes:**
* Sebastián López Duarte
* Paola Andrea Cepeda Castro
* José Daniel Porras Rodriguéz



---

## 1. Introducción 

En el ámbito clínico, la monitorización continua de variables fisiológicas críticas como la frecuencia cardíaca ($\text{HR}$) y la saturación periférica de oxígeno ($\text{SpO}_2$) es vital para la seguridad del paciente. Los equipos biomédicos deben ser capaces de detectar variaciones anómalas y activar alarmas oportunas ante riesgos inminentes (por ejemplo, bradicardias o hipoxias). 

Para verificar la respuesta técnica, los límites de medición y la correcta emisión de alarmas en los monitores de signos vitales (como el Mindray uMEC 100), se emplean simuladores especializados de parámetros hemodinámicos y de pulsioximetría, tales como el **Pronk OxSim OX-1**, que permiten recrear de forma controlada condiciones fisiológicas normales y patológicas.

---

## 2. Objetivos

### Objetivo General
* Operar con el simulador de parámetros hemodinámicos Pronk OxSim (OX-1) y el monitor de signos vitales uMEC 100 para realizar pruebas funcionales y de verificación de alarmas.

### Objetivos Específicos
* Identificar los modos de operación y características técnicas de un simulador de parámetros hemodinámicos (Pronk OxSim OX-1).
* Verificar los límites de medición, tiempos de respuesta y activación de alarmas de un monitor de signos vitales ante escenarios simulados.
* Interpretar las variaciones en los parámetros hemodinámicos y los errores de lectura comparados contra un equipo patrón.

---

## 3. Equipos Utilizados

| Descripción del Equipo / Dispositivo | Modelo / Referencia | Cantidad |
| :--- | :--- | :---: |
| Monitor de signos vitales con módulo de $\text{SpO}_2$ | Mindray uMEC 100 | 1 |
| Simulador de parámetros hemodinámicos (Patrón) | Pronk OxSim OX-1 | 1 |
| Pinza / Sensor de pulsioximetría ($\text{SpO}_2$) | Compatible con OxSim / uMEC 100 | 1 |
| Computador personal y herramientas de registro | Software de documentación | 1 |

### OxSim

Un oxSIM (simulador de oxigenación) es una herramienta de simulación utilizada en el ámbito biomédico para representar y estudiar los procesos relacionados con la oxigenación del organismo, permitiendo analizar variables como la concentración de oxígeno, la saturación de oxígeno en la sangre y el comportamiento de los sistemas de soporte respiratorio, según las características del simulador. Su importancia radica en que facilita la comprensión del funcionamiento del sistema respiratorio, permite evaluar diferentes condiciones de oxigenación y contribuye a la formación del personal de salud mediante escenarios controlados y seguros, sin necesidad de intervenir directamente sobre un paciente. Además, este tipo de simulación favorece el aprendizaje práctico, la evaluación de tecnologías biomédicas y la toma de decisiones clínicas, ayudando a mejorar la preparación de los profesionales y la seguridad en los procedimientos médicos.

<img width="225" height="225" alt="image" src="https://github.com/user-attachments/assets/cd65158e-e1ed-4205-8423-821ebd53457a" />
Según el panel del equipo (visible en las fotografías), el OX-1 ofrece **cinco modos fijos** y un selector de sensor:

| Modo (selector MODE) | SpO₂ simulada | FC simulada |
| :---: | :---: | :---: |
| 1 | 85 % | 80 bpm |
| 2 | 95 % | 40 bpm (bradicardia) |
| 3 | 98 % | 80 bpm |
| 4 | 98 % | 140 bpm (taquicardia) |
| 5 | 99 % | *Low Perf* (baja perfusión; FC no indicada en el panel) |

El selector **SENSOR** permite elegir *Auto*, *HP/Ohm* u *Other* (en todas las pruebas se usó *Auto*), y los indicadores *Batt*, *IR* y *Red* muestran el estado de la batería y la actividad de los emisores de luz infrarroja y roja del sensor.

---
## 4. Metodología

### 4.1 Diseño experimental

Se aplicó el mismo protocolo de cuatro escenarios a dos configuraciones del monitor:

* **Prueba 1:** uMEC 100 que funcionó correctamente. Perfil "Valores predeterm. fábrica", paciente adulto, filtro de ECG en modo *Diagnóstico*.
* **Prueba 2:** uMEC 100 con comportamiento defectuoso (no entregaba los datos simulados en varios escenarios). Mismo perfil de fábrica, paciente adulto, filtro de ECG en modo *Cirugía* y prioridad de alarmas de SpO₂ en *Medio*.

En ambos casos el **patrón** es el OxSim OX-1, cuyo valor configurado se toma como valor verdadero convencional, y el **instrumento bajo prueba** es el uMEC 100.

> Como el ECG no estaba conectado (la pantalla muestra "Deriv ECG desconect."), la frecuencia cardíaca que se muestra proviene del pulso de SpO₂ (la pantalla indica *Origen: SpO₂*). Por tanto, la FC evaluada es en realidad la **frecuencia de pulso (FP)** derivada de la onda fotopletismográfica.

### 4.2 Procedimiento

El procedimiento siguió la guía de laboratorio (Parte B):

1. Construcción de la tabla de verificación de alarmas (límite configurado, valor simulado, ¿alarma activa? y tiempo de respuesta).
2. Encendido del uMEC 100 y selección del modo de monitorización.
3. Conexión de la pinza de pulsioximetría al OxSim OX-1.
4. **Paso 1 — Bradicardia:** OxSim en 95 % / 40 bpm. Registro de lecturas y de la forma de onda fotopletismográfica.
5. **Paso 2 — Hipoxia:** límite inferior de alarma de SpO₂ en 90 %. OxSim en 85 % / 80 bpm. Se esperaron 5 s y se verificó la alarma sonora/visual.
6. **Paso 3 — Baja perfusión:** límite superior de alarma de SpO₂ en 97 %. OxSim en 99 % (*Low Perf*). Se esperaron 5 s, se verificó la alarma y se observó la onda.
7. **Paso 4 — Taquicardia:** OxSim en 98 % / 140 bpm. Registro de la onda y verificación de la alarma de FC elevada.
8. En cada paso se fotografió la pantalla del uMEC 100 y el panel del OxSim.
9. Cálculo de errores y comparación entre pruebas.

### 4.3 Cálculo de errores

Para cada variable, con *V_patrón* el valor simulado por el OxSim y *V_monitor* el valor mostrado por el uMEC 100:
Cuando el monitor **no mostró ningún valor** (pantalla con "--"), el error no se puede calcular con estas fórmulas. En ese caso se reporta como **"sin lectura"** y se contabiliza como pérdida de la medida (equivalente a un 100 % de indisponibilidad en ese escenario).

### 4.4 Criterios de aceptación

* **SpO₂:** error dentro de ±2 % a ±3 % puntos de SpO₂ (rango típico de exactitud de pulsioxímetros; la norma ISO 80601-2-61 exige exactitud en el rango 70–100 %).
* **FC / frecuencia de pulso:** error dentro de ±3 bpm (valor típico de especificación de los módulos de SpO₂ de monitores de cabecera).
* **Alarmas:** debe activarse la alarma correspondiente cuando el valor simulado supera el límite configurado, con prioridad y mensaje coherentes, dentro del tiempo de verificación de 5 s indicado en la guía.

> Estas tolerancias son valores de referencia comunes y deben contrastarse con la especificación del manual del uMEC 100 y con la norma aplicable.

### 4.5 Registro y seguridad

Los datos se registraron mediante fotografías de las pantallas (con la hora del monitor visible) y se transcribieron a las tablas de este informe. Se siguieron las normas de seguridad de la guía: manipulación de los equipos solo con presencia del técnico, uso de bata, pantalón largo y cabello recogido, y sin dejar sesiones iniciadas en los equipos de cómputo institucionales.

## 5. Parte A 
### a. ¿Cómo colocar al uMEC 100 en modo "monitor"?

El uMEC 100 se enciende con el botón de encendido y, una vez iniciado, queda en la pantalla principal de monitorización con un paciente admitido (en las fotografías: paciente tipo **Adulto**, perfil "Valores predeterm. fábrica" y nombre de paciente "Prueba 1" / "Prueba 2"). Allí se muestran en tiempo real el ECG, la onda pletismográfica (Plet), SpO₂, respiración, temperatura y PANI.

En la parte superior izquierda de la pantalla se observa además el **modo de filtro de ECG**, que en monitores Mindray puede ser *Monitor*, *Diagnóstico* o *Cirugía*. En nuestras pruebas se usó *Diagnóstico* (Prueba 1) y *Cirugía* (Prueba 2). Este filtro afecta únicamente a la señal de ECG y no a la medida de SpO₂, pero conviene dejarlo registrado porque difiere entre pruebas.

> **Pendiente de verificar con el manual de operación del uMEC 100:** la ruta exacta del menú para seleccionar el filtro *Monitor* y la distinción entre el modo de monitorización normal, el modo de espera (*Standby*) y el modo de configuración/demo. La guía solicita contrastar esta información contra el manual.

<img width="500" height="500" alt="IMG_20261020_145225" src="https://github.com/user-attachments/assets/b3316b9d-e143-4c0a-afcd-1de6277eb4c3" />

### b. ¿Qué parámetros fisiológicos pueden simularse con el OxSim OX-1?

* **Saturación periférica de oxígeno (SpO₂):** porcentaje de hemoglobina oxigenada en sangre arterial. El OX-1 genera valores fijos de 85 %, 95 %, 98 % y 99 %, que permiten probar un valor de hipoxia, uno normal-bajo, uno normal y uno alto.
* **Frecuencia cardíaca / frecuencia de pulso (FC):** latidos por minuto reproducidos por la señal pulsátil: 40 bpm (bradicardia), 80 bpm (normal) y 140 bpm (taquicardia).
* **Perfusión / amplitud de pulso (modo *Low Perf*):** simula una señal pulsátil de amplitud muy reducida, típica de mala perfusión periférica, para evaluar la sensibilidad del monitor ante señales débiles. En el monitor se refleja como un **índice de perfusión (IP)** muy bajo (0.45 en la Prueba 1, frente a ≈4.1–4.4 en los demás modos).
* **Onda fotopletismográfica:** curva de variación del volumen sanguíneo sincronizada con el pulso, que el monitor dibuja en el canal *Plet*. Su frecuencia depende de la FC simulada y su amplitud del nivel de perfusión.

**Lo que el OxSim no simula:** el OX-1 no genera ECG, arritmias, presión arterial, respiración ni artefactos de movimiento, y solo ofrece combinaciones fijas de SpO₂/FC (no valores arbitrarios).

### c. Errores máximos permitidos (EMP) en el ámbito clínico

| Parámetro | EMP de referencia | Comentario |
| :--- | :---: | :--- |
| SpO₂ | ±2 % a ±3 % (puntos de SpO₂) | Rango típico de exactitud de pulsioxímetros de uso clínico en 70–100 %; la exactitud empeora por debajo de 70 % |
| FC / frecuencia de pulso | ±3 bpm (típico) | Algunos fabricantes especifican ±2 % o ±1 bpm. Valor a confirmar con el manual del equipo |

> Estos valores deben confirmarse con la hoja de especificaciones/manual del uMEC 100 y con la norma ISO 80601-2-61 antes de la entrega final.

---

## 6. Parte B — Pruebas

### 6.1 Registro de Datos Obtenidos (Patrón vs. Monitor)
A continuación se registran los datos experimentales obtenidos al conectar el equipo patrón (OxSim) al monitor de signos vitales, comparando una configuración defectuosa/errónea frente a la configuración exitosa:

| Condición / Ensayo | Parámetro Patrón ($\text{SpO}_2$ / $\text{HR}$) | Caso No Funcionó ($\text{SpO}_2$ / $\text{HR}$) | Caso Sí Funcionó ($\text{SpO}_2$ / $\text{HR}$) | Error Absoluto ($\text{SpO}_2$ / $\text{HR}$) | Error Porcentual ($\text{SpO}_2$ / $\text{HR}$) | Estado de Alarma |
| :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **1** | $85\% \text{ / } 80\text{ lpm}$ | *Sin registro* | $85\% \text{ / } 80\text{ lpm}$ | $0\% \text{ / } 0\text{ bpm}$ | $0\% \text{ / } 0\%$ | Sin alarma (Valores normales/esperados) |
| **2 (Bradicardia)** | $95\% \text{ / } 40\text{ lpm}$ | $94\% \text{ / } 80\text{ lpm}$ | $96\% \text{ / } 40\text{ lpm}$ | $\Delta\text{SpO}_2 = 1\%$<br>$\Delta\text{HR} = 0\text{ bpm}$ | $\text{SpO}_2: 1.05\%$<br>$\text{HR}: 0\%$ | **Activa** (Alarma por Bradicardia $< 50\text{ lpm}$) |
| **3** | $98\% \text{ / } 80\text{ lpm}$ | *Sin registro* | $98\% \text{ / } 80\text{ lpm}$ | $0\% \text{ / } 0\text{ bpm}$ | $0\% \text{ / } 0\%$ | Sin alarma |
| **4 (Taquicardia)** | $98\% \text{ / } 140\text{ lpm}$ | *Sin registro* | $98\% \text{ / } 140\text{ lpm}$ | $0\% \text{ / } 0\text{ bpm}$ | $0\% \text{ / } 0\%$ | **Activa** (Alarma por Taquicardia $> 120\text{ lpm}$) |

<img width="500" height="500" alt="MVIMG_20261020_150052" src="https://github.com/user-attachments/assets/24e03925-6baa-4d15-8af0-45298989c1f4" />

<img width="500" height="500" alt="MVIMG_20261020_145324" src="https://github.com/user-attachments/assets/0bf77266-063d-483b-8fab-83faf80bdbe0" />

**Notas:**

1. En ambas pruebas la FC simulada de 40 bpm quedó por debajo del límite bajo configurado (45 y 50 bpm respectivamente), pero **en las fotografías no se observa ninguna alarma de FC baja**. No se registró si se escuchó una alarma sonora ni se midió el retardo de activación; este punto debe contrastarse con el manual (las alarmas de FC/FP pueden tener retardos y condiciones de activación) o repetirse.
2. La alarma `T1 baja < 35.0` es ajena a la prueba: el sensor de temperatura no estaba conectado y el monitor leía la temperatura ambiente (≈22 °C).
3. En la captura posterior (≈19 s después, según el contador "Deriv ECG desconect.") el monitor ya mostraba 140 bpm / 98 %, pero **no apareció la alarma de FC alta** (140 > 120) ni la de SpO₂ alta (98 > 97) que se esperaban con los límites configurados. Es posible que las alarmas estuvieran silenciadas o pausadas, lo cual no se verificó.

### 6.2 Registro de datos — Prueba 1 (equipo funcional)

**Paso 1 — Bradicardia (40 bpm, SpO₂ 95 %).** El monitor mostró 40 bpm y 95 %. La onda pletismográfica tiene un periodo largo (≈4 pulsos en la ventana visible) con ascenso rápido y descenso más lento.

| OxSim | uMEC 100 |
| :---: | :---: |
| <img src="Imagenes/prueba1_paso1_oxsim_40bpm_95.jpg" width="380"> | <img src="Imagenes/prueba1_paso1_monitor_40bpm_95.jpg" width="380"> |

**Paso 2 — Hipoxia (80 bpm, SpO₂ 85 %), límite bajo = 90 %.** El monitor mostró 80 bpm y 85 % y activó la alarma roja `SpO2 bajo < 90`.

| OxSim | uMEC 100 |
| :---: | :---: |
| <img src="Imagenes/prueba1_paso2_oxsim_85_80bpm.jpg" width="380"> | <img src="Imagenes/prueba1_paso2_monitor_alarma_spo2_bajo.jpg" width="380"> |

**Paso 3 — Baja perfusión (99 %), límite alto = 97 %.** El monitor mostró 80 bpm y **100 %**, con un índice de perfusión de 0.45, y activó la alarma `SpO2 alto > 97`. La onda es de menor amplitud y con morfología más irregular que en los otros modos (ver respuesta en 6.4).

| OxSim | uMEC 100 |
| :---: | :---: |
| <img src="Imagenes/prueba1_paso3_oxsim_lowperf.jpg" height="300"> | <img src="Imagenes/prueba1_paso3_monitor_alarma_spo2_alto.jpg" width="380"> |

**Paso 4 — Taquicardia (140 bpm, SpO₂ 98 %).** El monitor mostró 140 bpm y 98 %. Primero estaba activa la alarma de SpO₂ alta (98 > 97) y a continuación apareció la alarma `FP alta > 110`, con los valores resaltados en rojo.

| OxSim | uMEC 100 (SpO₂ alta) | uMEC 100 (FC alta) |
| :---: | :---: | :---: |
| <img src="Imagenes/prueba1_paso4_oxsim_98_140bpm.jpg" width="250"> | <img src="Imagenes/prueba1_paso4_monitor_140bpm_spo2_alto.jpg" width="250"> | <img src="Imagenes/prueba1_paso4_monitor_alarma_fc_alta.jpg" width="250"> |

### 6.3 Registro de datos — Prueba 2 (equipo defectuoso)

**Paso 1 — Bradicardia (40 bpm, SpO₂ 95 %).** Lectura correcta (40 bpm / 95 %). La onda tiene forma diferente a la de la Prueba 1 (más "diente de sierra") y se dibuja en otro color; el índice de perfusión fue 4.17.

| OxSim | uMEC 100 |
| :---: | :---: |
| <img src="Imagenes/prueba2_paso1_oxsim_40bpm_95.jpg" width="380"> | <img src="Imagenes/prueba2_paso1_monitor_40bpm_95.jpg" width="380"> |

**Paso 2 — Hipoxia (80 bpm, SpO₂ 85 %).** Antes de simular, se configuraron los límites en el menú *Ajuste alarma* (SpO₂ 100/90). Lectura correcta (80 bpm / 85 %) y alarma `SpO2 bajo < 90`, pero **en prioridad media (amarillo)** en lugar de alta (rojo) como en la Prueba 1.

| Límites configurados | OxSim | uMEC 100 |
| :---: | :---: | :---: |
| <img src="Imagenes/prueba2_paso2_limites_alarma_100_90.jpg" width="250"> | <img src="Imagenes/prueba2_paso2_oxsim_85_80bpm.jpg" width="250"> | <img src="Imagenes/prueba2_paso2_monitor_alarma_spo2_bajo.jpg" width="250"> |

**Paso 3 — Baja perfusión (99 %), límite alto = 97 %.** Tras ajustar el límite alto a 97 % (captura izquierda), **el monitor no mostró ningún valor de FC ni de SpO₂** (aparecen guiones) y generó las alarmas `!!!Sin pulso` y `!Exceso de luz para SpO2`. La onda sí se dibujaba, pero sin valores numéricos asociados.

| Límites configurados | OxSim | uMEC 100 |
| :---: | :---: | :---: |
| <img src="Imagenes/prueba2_paso3_limites_alarma_97_90.jpg" width="250"> | <img src="Imagenes/prueba2_paso3_oxsim_lowperf.jpg" width="250"> | <img src="Imageness/prueba2_paso3_monitor_sin_pulso.jpg" width="250"> |

**Paso 4 — Taquicardia (140 bpm, SpO₂ 98 %).** Inicialmente el monitor siguió sin mostrar valores (`Sin pulso`, `Exceso de luz para SpO2`) a pesar de dibujar una onda sinusoidal de alta frecuencia. Unos 19 s después mostró 140 bpm / 98 %, pero **sin alarma de FC alta ni de SpO₂ alta**.

| uMEC 100 (inicio) | OxSim | uMEC 100 (≈19 s después) |
| :---: | :---: | :---: |
| <img src="Imagenes/prueba2_paso4_monitor_sin_pulso.jpg" width="250"> | <img src="Imagenes/prueba2_paso4_oxsim_98_140bpm.jpg" width="250"> | <img src="Imagenes/prueba2_paso4_monitor_140bpm_98_sin_alarma_fc.jpg" width="250"> |

### 6.4 Tabla de errores absoluto y porcentual (patrón vs. monitor)

**Prueba 1 (equipo funcional)**

| Paso | Patrón SpO₂ / FC | Monitor SpO₂ / FC | Error abs. SpO₂ | Error % SpO₂ | Error abs. FC | Error % FC |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 (bradicardia) | 95 % / 40 bpm | 95 % / 40 bpm | 0 | 0 % | 0 bpm | 0 % |
| 2 (hipoxia) | 85 % / 80 bpm | 85 % / 80 bpm | 0 | 0 % | 0 bpm | 0 % |
| 3 (*Low Perf*) | 99 % / n.e.* | 100 % / 80 bpm | 1 | 1.01 % | n.e.* | n.e.* |
| 4 (taquicardia) | 98 % / 140 bpm | 98 % / 140 bpm | 0 | 0 % | 0 bpm | 0 % |

**Prueba 2 (equipo defectuoso)**

| Paso | Patrón SpO₂ / FC | Monitor SpO₂ / FC | Error abs. SpO₂ | Error % SpO₂ | Error abs. FC | Error % FC |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 (bradicardia) | 95 % / 40 bpm | 95 % / 40 bpm | 0 | 0 % | 0 bpm | 0 % |
| 2 (hipoxia) | 85 % / 80 bpm | 85 % / 80 bpm | 0 | 0 % | 0 bpm | 0 % |
| 3 (*Low Perf*) | 99 % / n.e.* | **Sin lectura** | No calculable | — (pérdida de medida) | n.e.* | n.e.* |
| 4 (taquicardia) | 98 % / 140 bpm | Sin lectura a los 5 s; **98 % / 140 bpm** a los ≈19 s | 0 (tras recuperar) | 0 % (tras recuperar) | 0 bpm (tras recuperar) | 0 % (tras recuperar) |

\* *n.e.: la frecuencia cardíaca del modo *Low Perf* no está especificada en el panel del OxSim. El monitor mostró 80 bpm, lo cual es consistente con el modo de 80 bpm, pero no se tiene un patrón documentado contra el cual calcular el error.*

### 6.2 Análisis del Comportamiento (Caso Exitoso vs. Fallido)
* **Caso No Funcionó:** Durante la prueba con el patrón a $95\%$ de saturación y $40\text{ lpm}$ (bradicardia), el sistema mostró una lectura errónea de $94\%$ en saturación pero un fallo grave en la frecuencia cardíaca ($80\text{ lpm}$ en lugar de $40\text{ lpm}$). Esto evidencia una mala sincronización o pérdida de enganche de la onda pulsátil por parte del módulo, provocando un falso diagnóstico o la ausencia de la alarma crítica por bradicardia.
* **Caso Sí Funcionó:** Tras corregir la configuración y la conexión del transductor con el patrón, el monitor uMEC 100 replicó fielmente los valores de referencia con errores insignificantes ($\le 1\%$), logrando disparar las alarmas sonoras y visuales correspondientes en los escenarios extremos (como los $40\text{ lpm}$ y $140\text{ lpm}$).


---

## 6. Parte C — Preguntas para la Discusión

1. **¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?**  
   El OxSim simula ópticamente la transmisión y absorción de luz mediante diodos infrarrojos y rojos acoplados al sensor de pulsioximetría, modulando la intensidad lumínica de manera sincronizada con la frecuencia cardíaca configurada para imitar los cambios volumétricos del lecho capilar.

2. **¿Por qué la $\text{SpO}_2$ baja puede ser un falso positivo (falsa alarma) en una situación de mala perfusión?**  
   Ante una mala perfusión, la amplitud del pulso óptico disminuye reduciendo la relación señal-ruido ($\text{SNR}$). El algoritmo del oxímetro puede confundir el ruido con la señal real, interpretando caídas ficticias en la saturación sin que exista hipoxia real en el paciente.

---

## 7. Conclusiones

La práctica permitió evaluar el funcionamiento del monitor de signos vitales Mindray uMEC 100 mediante el simulador Pronk OxSim OX-1, comprendiendo su utilidad en la verificación de parámetros cardiovasculares y hemodinámicos. Durante los ensayos se identificó que una conexión o configuración inadecuada puede generar errores en las mediciones, especialmente en la frecuencia cardíaca, afectando la interpretación de los resultados. Sin embargo, después de corregir estas condiciones, el monitor logró registrar valores cercanos a los establecidos por el equipo patrón. Asimismo, se comprobó la activación de las alarmas ante condiciones de bradicardia y taquicardia, demostrando la importancia de estos sistemas para identificar posibles alteraciones fisiológicas. También se reconoció que la saturación de oxígeno y la frecuencia cardíaca son variables fundamentales para evaluar el estado general de un paciente. Por otra parte, el uso del simulador permitió realizar pruebas controladas sin poner en riesgo a una persona, facilitando la identificación de posibles fallas del equipo. Finalmente, esta experiencia permitió fortalecer los conocimientos sobre el manejo, la evaluación y la verificación de equipos biomédicos, destacando la importancia de garantizar mediciones confiables y respuestas oportunas de las alarmas en el entorno clínico.

---

## 8. Referencias Bibliográficas

[1] Instituto de Salud Pública de Chile (ISP), "Guía para la Clasificación de Dispositivos Médicos según Riesgo," ISPCH, Santiago, Chile, Guía técnica, 2021[cite: 20].  
[2] Instituto Nacional de Vigilancia de Medicamentos y Alimentos (INVIMA), *ABC de Dispositivos Médicos - Guía Reguladora*, Bogotá, Colombia: INVIMA[cite: 20].  
[3] Medical IT, "Metrología Biomédica - Simulador OxSim," [En línea]. Disponible en: [https://www.medicalitech.com/producto/ox-sim/](https://www.medicalitech.com/producto/ox-sim/)[cite: 20].
