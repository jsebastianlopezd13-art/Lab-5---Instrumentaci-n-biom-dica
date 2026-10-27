# Laboratorio 5: Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

**Asignatura:** Instrumentación Biomédica y Biosensores  
**Docente:** Ing. Alejandra Rosero Cárdenas / Equipo Académico  
**Integrantes / Colaboradores del Repositorio:**
* Sebastián López Duarte
* [Nombre Estudiante 2]
* [Nombre Estudiante 3]



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

## 3. Equipos e Instrumentación Utilizada

| Descripción del Equipo / Dispositivo | Modelo / Referencia | Cantidad |
| :--- | :--- | :---: |
| Monitor de signos vitales con módulo de $\text{SpO}_2$ | Mindray uMEC 100 | 1 |
| Simulador de parámetros hemodinámicos (Patrón) | Pronk OxSim OX-1 | 1 |
| Pinza / Sensor de pulsioximetría ($\text{SpO}_2$) | Compatible con OxSim / uMEC 100 | 1 |
| Computador personal y herramientas de registro | Software de documentación | 1 |

---

## 4. Parte A — Marco Teórico y Cuestionario

### a. ¿Cómo colocar al uMEC 100 en modo "monitor"?
Para configurar el monitor Mindray uMEC 100 en modo operativo de monitorización clínica estándar ("Monitor Mode"), se enciende el equipo mediante el botón principal y se accede al menú de configuración del sistema (Setup Mode), seleccionando perfiles predeterminados para pacientes adultos/pediátricos y asegurando la adquisición en tiempo real desde el puerto de la sonda de $\text{SpO}_2$.

### b. ¿Qué tipo de parámetros o variables fisiológicas pueden simularse con el Pronk OxSim OX-1? Explique cada una.
* **Frecuencia Cardíaca ($\text{HR}$):** Simulación de latidos por minuto en rangos de bradicardia, normocardia y taquicardia.
* **Saturación Periférica de Oxígeno ($\text{SpO}_2$):** Porcentaje de oxigenación de la hemoglobina arterial.
* **Perfusión / Amplitud de Pulso:** Simulación de baja perfusión periférica para evaluar la sensibilidad del sensor ante señales débiles.
* **Onda Fotopletismográfica:** Reproducción óptica de la curva de volumen sanguíneo sincronizada con el pulso.

### c. En el ámbito clínico, ¿cuáles son los errores máximos permitidos (EMP) para cada parámetro?
* **Frecuencia Cardíaca:** Error permitido de $\pm 1\%$ o $\pm 1\text{ bpm}$ frente al patrón.
* **Saturación de Oxígeno ($\text{SpO}_2$):** Tolerancia clínica estándar de $\pm 2\%$ a $\pm 3\%$ en el intervalo operativo.

---

## 5. Parte B — Pruebas Funcionales y Toma de Datos

### 5.1 Registro de Datos Obtenidos (Patrón vs. Monitor)
A continuación se registran los datos experimentales obtenidos al conectar el equipo patrón (OxSim) al monitor de signos vitales, comparando una configuración defectuosa/errónea frente a la configuración exitosa:

| Condición / Ensayo | Parámetro Patrón ($\text{SpO}_2$ / $\text{HR}$) | Caso No Funcionó ($\text{SpO}_2$ / $\text{HR}$) | Caso Sí Funcionó ($\text{SpO}_2$ / $\text{HR}$) | Error Absoluto ($\text{SpO}_2$ / $\text{HR}$) | Error Porcentual ($\text{SpO}_2$ / $\text{HR}$) | Estado de Alarma |
| :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **1** | $85\% \text{ / } 80\text{ lpm}$ | *Sin registro* | $85\% \text{ / } 80\text{ lpm}$ | $0\% \text{ / } 0\text{ bpm}$ | $0\% \text{ / } 0\%$ | Sin alarma (Valores normales/esperados) |
| **2 (Bradicardia)** | $95\% \text{ / } 40\text{ lpm}$ | $94\% \text{ / } 80\text{ lpm}$ | $96\% \text{ / } 40\text{ lpm}$ | $\Delta\text{SpO}_2 = 1\%$<br>$\Delta\text{HR} = 0\text{ bpm}$ | $\text{SpO}_2: 1.05\%$<br>$\text{HR}: 0\%$ | **Activa** (Alarma por Bradicardia $< 50\text{ lpm}$) |
| **3** | $98\% \text{ / } 80\text{ lpm}$ | *Sin registro* | $98\% \text{ / } 80\text{ lpm}$ | $0\% \text{ / } 0\text{ bpm}$ | $0\% \text{ / } 0\%$ | Sin alarma |
| **4 (Taquicardia)** | $98\% \text{ / } 140\text{ lpm}$ | *Sin registro* | $98\% \text{ / } 140\text{ lpm}$ | $0\% \text{ / } 0\text{ bpm}$ | $0\% \text{ / } 0\%$ | **Activa** (Alarma por Taquicardia $> 120\text{ lpm}$) |

### 5.2 Análisis del Comportamiento (Caso Exitoso vs. Fallido)
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

* La implementación de pruebas funcionales usando el simulador Pronk OxSim como patrón permitió contrastar de forma directa el comportamiento operativo del monitor uMEC 100, identificando fallas de lectura ante configuraciones deficientes.
* Se comprobó que cuando el sistema funciona correctamente, los errores de medición son mínimos ($\le 1\%$), garantizando una alta confiabilidad en la emisión oportuna de alarmas clínicas ante eventos de taquicardia y bradicardia.

---

## 8. Referencias Bibliográficas

[1] Instituto de Salud Pública de Chile (ISP), "Guía para la Clasificación de Dispositivos Médicos según Riesgo," ISPCH, Santiago, Chile, Guía técnica, 2021[cite: 20].  
[2] Instituto Nacional de Vigilancia de Medicamentos y Alimentos (INVIMA), *ABC de Dispositivos Médicos - Guía Reguladora*, Bogotá, Colombia: INVIMA[cite: 20].  
[3] Medical IT, "Metrología Biomédica - Simulador OxSim," [En línea]. Disponible en: [https://www.medicalitech.com/producto/ox-sim/](https://www.medicalitech.com/producto/ox-sim/)[cite: 20].
