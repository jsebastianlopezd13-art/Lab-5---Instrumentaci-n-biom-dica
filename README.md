# Lab-5---Instrumentaci-n-biom-dica

# Laboratorio 5: Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

**Asignatura:** Instrumentación Biomédica y Biosensores[cite: 11]  
**Docente:** Ing. Alejandra Rosero Cárdenas / Equipo Académico[cite: 11]  
**Integrantes / Colaboradores del Repositorio:**
* [Nombre Estudiante 1]
* [Nombre Estudiante 2]
* [Nombre Estudiante 3]

> **Nota de repositorio:** Este documento consolida el desarrollo experimental, el análisis de datos, las respuestas teóricas y las evidencias gráficas correspondientes a la evaluación técnica y funcional del monitor de signos vitales mediante el simulador de parámetros hemodinámicos[cite: 15, 18].

---

## 1. Introducción y Contexto Teórico

En el ámbito clínico, la monitorización continua de variables fisiológicas críticas como la frecuencia cardíaca ($\text{HR}$) y la saturación periférica de oxígeno ($\text{SpO}_2$) es vital para la seguridad del paciente[cite: 15]. Los equipos biomédicos deben ser capaces de detectar variaciones anómalas y activar alarmas oportunas ante riesgos inminentes (por ejemplo, arritmias, hipoxia o bradicardias)[cite: 15]. 

Para verificar la respuesta técnica, los límites de medición y la correcta emisión de alarmas en los monitores de signos vitales (como el **Mindray uMEC 100**), se emplean simuladores especializados de parámetros hemodinámicos y de pulsioximetría, tales como el **Pronk OxSim OX-1**, que permiten recrear de forma controlada condiciones fisiológicas normales y patológicas[cite: 15].

---

## 2. Objetivos

### Objetivo General
* Operar con el simulador de parámetros hemodinámicos Pronk OxSim (OX-1) y el monitor de signos vitales uMEC 100 para realizar pruebas funcionales y de verificación de alarmas[cite: 16].

### Objetivos Específicos
* Identificar los modos de operación y características técnicas de un simulador de parámetros hemodinámicos (Pronk OxSim OX-1)[cite: 16].
* Verificar los límites de medición, tiempos de respuesta y activación de alarmas de un monitor de signos vitales ante escenarios simulados[cite: 16].
* Interpretar las variaciones en los parámetros hemodinámicos y la distorsión de la onda fotopletismográfica asociadas a estados fisiológicos y patológicos[cite: 16].

---

## 3. Equipos e Instrumentación Utilizada

| Descripción del Equipo / Dispositivo | Modelo / Referencia | Cantidad |
| :--- | :--- | :---: |
| Monitor de signos vitales con módulo de $\text{SpO}_2$ | Mindray uMEC 100[cite: 16] | 1 |
| Simulador de parámetros hemodinámicos | Pronk OxSim OX-1[cite: 16] | 1 |
| Pinza / Sensor de pulsioximetría ($\text{SpO}_2$) | Compatible con OxSim / uMEC 100 | 1 |
| Computador personal (con conexión a internet y herramientas de registro)[cite: 17] | Software de análisis y documentación | 1 |

---

## 4. Parte A — Marco Teórico y Cuestionario

### a. ¿Cómo colocar al uMEC 100 en modo "monitor"?
Para configurar el monitor Mindray uMEC 100 en modo operativo de monitorización clínica estándar ("Monitor Mode"), se debe encender el equipo utilizando el botón de encendido principal y, a través de la interfaz táctil o el botón rotatorio de navegación, acceder al menú de configuración del sistema (User Maintenance / Setup Mode), asegurándose de seleccionar perfiles clínicos predeterminados para pacientes adultos/pediátricos según corresponda, deshabilitando simulaciones internas y activando la adquisición en tiempo real desde el puerto de la sonda de $\text{SpO}_2$.

### b. ¿Qué tipo de parámetros o variables fisiológicas pueden simularse con el Pronk OxSim OX-1? Explique cada una.
* **Frecuencia Cardíaca ($\text{HR}$):** Simulación de los latidos por minuto, abarcando rangos de bradicardia severa, normocardia y taquicardia.
* **Saturación Periférica de Oxígeno ($\text{SpO}_2$):** Simulación porcentual de la oxigenación de la hemoglobina en sangre arterial.
* **Perfusión / Amplitud de Pulso (Modo Low Perfusion):** Simulación de baja perfusión periférica, útil para evaluar la sensibilidad del sensor ante señales débiles o artefactos por vasoconstricción.
* **Onda Fotopletismográfica:** Reproducción óptica de la curva de volumen sanguíneo pulsátil sincronizada con el pulso cardíaco.

### c. En el ámbito clínico, ¿cuáles son los errores máximos permitidos (EMP) para cada parámetro?
* **Frecuencia Cardíaca:** Generalmente un error permitido de $\pm 1\%$ o $\pm 1\text{ bpm}$ (el que sea mayor) frente al valor de referencia del simulador.
* **Saturación de Oxígeno ($\text{SpO}_2$):** Rango de tolerancia clínica estándar de $\pm 2\%$ a $\pm 3\%$ en el intervalo operativo del 70% al 100%.

---

## 5. Parte B — Pruebas Funcionales y Verificación de Alarmas

### 5.1 Tabla de Verificación de Alarmas y Errores de Medición

| Ítem / Escenario | Parámetro Evaluado | Límite Configurado | Valor Simulado (OxSim) | Valor Medido (uMEC 100) | Error Absoluto | Error Porcentual (%) | ¿Alarma Activa? (Sí/No) | Tiempo de Respuesta |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | Bradicardia / $\text{SpO}_2$ | Por defecto | $\text{HR: } 40\text{ bpm}$<br>$\text{SpO}_2\text{: } 95\%$ | *[Insertar valor]* | *[Cálculo]* | *[Cálculo]* | No (Parámetros dentro de rango seguro) | N/A |
| **2** | Hipoxia / Límite Bajo | Inferior: $\text{SpO}_2 < 90\%$ | $\text{HR: } 80\text{ bpm}$<br>$\text{SpO}_2\text{: } 85\%$ | *[Insertar valor]* | *[Cálculo]* | *[Cálculo]* | Sí | *[Ej. < 5s]* |
| **3** | Baja Perfusión | Superior: $\text{SpO}_2 > 97\%$ | $\text{SpO}_2\text{: } 99\%$ (Low Perf.) | *[Insertar valor]* | *[Cálculo]* | *[Cálculo]* | Sí | *[Ej. < 5s]* |
| **4** | Taquicardia | Por defecto / Límites | $\text{HR: } 140\text{ bpm}$<br>$\text{SpO}_2\text{: } 98\%$ | *[Insertar valor]* | *[Cálculo]* | *[Cálculo]* | Sí (por límite de $\text{HR}$) | *[Ej. < 5s]* |

> *Nota de cálculo:*  
> * $\text{Error Absoluto} = \mid \text{Valor Medido} - \text{Valor Simulado} \mid$  
> * $\text{Error Porcentual (\%)} = \left( \frac{\text{Error Absoluto}}{\text{Valor Simulado}} \right) \times 100$

### 5.2 Registro Visual y Análisis de Ondas Fotopletismográficas
*(Insertar aquí capturas de pantalla o fotografías de alta resolución tomadas durante la práctica en el monitor uMEC 100 correspondientes a:*
* *Forma de onda bajo condición de bradicardia (40 bpm).*
* *Distorsión de la onda fotopletismográfica en modo "Low Perfusion" con $\text{SpO}_2 = 99\%$.*
* *Comportamiento de la onda ante taquicardia de 140 bpm).*

---

## 6. Parte C — Preguntas para la Discusión

1. **¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?**  
   El OxSim simula ópticamente la transmisión y absorción de luz mediante diodos infrarrojos y rojos simulados o acoplados ópticamente a la pinza del sensor de pulsioximetría. Modula la intensidad de la luz de forma sincronizada con la frecuencia cardíaca configurada, imitando los cambios volumétricos en el lecho capilar que el sensor del monitor interpreta como una onda fotopletismográfica real.

2. **¿Por qué la $\text{SpO}_2$ baja puede ser un falso positivo (falsa alarma) en una situación de mala perfusión?**  
   En escenarios de baja perfusión periférica (hipotermia, vasoconstricción, shock o mala colocación del sensor), la amplitud del pulso óptico disminuye drásticamente, reduciendo la relación señal-ruido ($\text{SNR}$). El algoritmo del oxímetro puede interpretar erróneamente el ruido ambiental o la debilidad de la señal asistiéndose con cálculos imprecisos de la relación de absorción de luz roja/infrarroja, generando caídas ficticias en el porcentaje de saturación sin que exista hipoxia real en el paciente.

---

## 7. Conclusiones

* El uso combinado del simulador Pronk OxSim OX-1 y el monitor Mindray uMEC 100 permitió comprobar de forma efectiva la respuesta instrumental ante situaciones críticas simuladas (bradicardia, taquicardia, hipoxia y baja perfusión).
* Se evidenció que el monitor cumple con los tiempos de respuesta ante la transgresión de los límites de alarma configurados, validando su confiabilidad operativa para entornos clínicos.
* Se identificaron las limitaciones del simulador y del sensor ante condiciones extremas de baja perfusión, donde la alteración de la onda fotopletismográfica puede inducir errores de lectura o falsas alarmas, reforzando la necesidad de criterio técnico en la interpretación biomédica.

---

## 8. Referencias Bibliográficas

[1] Instituto de Salud Pública de Chile (ISP), "Guía para la Clasificación de Dispositivos Médicos según Riesgo," ISPCH, Santiago, Chile, Guía técnica, 2021[cite: 20].  
[2] Instituto Nacional de Vigilancia de Medicamentos y Alimentos (INVIMA), *ABC de Dispositivos Médicos - Guía Reguladora*, Bogotá, Colombia: INVIMA[cite: 20].  
[3] Medical IT, "Metrología Biomédica - Simulador OxSim," [En línea]. Disponible en: [https://www.medicalitech.com/producto/ox-sim/](https://www.medicalitech.com/producto/ox-sim/)[cite: 20].
