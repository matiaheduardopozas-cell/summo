# 🧮 Guía Práctica del Módulo Matemático de Summo
> **Proyecto ABPro — Funciones y Matrices (MVFM01) · INACAP**  
> **Integrantes:** Damián Xu & Matías Eduardo Pozas Arias  
> **Docente:** Jaime Patricio Lazo Sáez  

Esta guía explica en palabras sencillas cómo funciona el nuevo módulo matemático integrado en **Summo**, cómo acceder a él en cualquier momento y qué responder ante las preguntas del profesor o durante la grabación del video de la **Etapa 3**.

---

## 🚀 1. ¿Cómo ingresar al módulo?

Tienes dos formas de abrirlo sin tocar tus finanzas personales:

1. **Acceso directo por URL (Recomendado para la presentación/video):**
   - Módulo matemático completo: [https://summo-wallet.web.app/?demo=math](https://summo-wallet.web.app/?demo=math)
   - Vista directa de la matriz de desviación ($D = P - M$): [https://summo-wallet.web.app/?demo=dev](https://summo-wallet.web.app/?demo=dev)
2. **Desde el login de la app:**
   - Entra a [https://summo-wallet.web.app](https://summo-wallet.web.app).
   - En la pantalla de bienvenida, haz clic en el botón con borde punteado:  
     `🧪 Modo Simulación Académica (ABPro)`.
   - Luego toca la pestaña **`🧮 Modelo`** en el menú de navegación.

*(Nota: Todo lo que hagas en el modo simulación se guarda temporalmente en la memoria del navegador. Puedes agregar, editar o borrar gastos y el modelo matemático se recalculará en tiempo real sin modificar tu base de datos en Google Cloud).*

---

## 🧩 2. ¿Qué hace cada sección del módulo matemático?

El módulo traduce los gastos registrados a la materia de la **Unidad 3**:

### A. Matriz Presupuestaria Categoría × Semana ($M_{4\times 4}$)
* **¿Qué es?**  
  Una matriz matemática de 4 filas (las 4 macrocategorías de gasto) y 4 columnas (Semana 1, Semana 2, Semana 3 y Semana 4 del mes).
* **Las 3 vistas interactivas (botones superiores):**
  1. **Gasto Real ($M$):** Muestra el dinero efectivamente gastado en cada casilla $m_{ij}$.  
     Al costado derecho calcula el producto matriz-vector $\mathbf{g} = M \cdot \mathbf{u}$ (donde $\mathbf{u} = [1, 1, 1, 1]^T$). Esto entrega el gasto mensual total por categoría y su porcentaje del presupuesto.
  2. **Meta ($P$ · Editable):** Es la matriz con el presupuesto ideal planificado para cada semana. Puedes hacer clic en cualquier casilla y cambiar el monto para probar distintos presupuestos.
  3. **Desviación ($D = P - M$):** Resta la matriz de metas menos la matriz de gastos reales.  
     - Si el resultado es **positivo (verde con ✓)**: Gastaste menos de lo presupuestado (ahorro semanal).
     - Si el resultado es **negativo (rojo con ⚠️)**: Tuviste un sobregiro en esa categoría y semana.  
     *(Ejemplo en el caso de estudio: Alimentación en la Semana 3 tuvo un sobregiro de $-\$4.000$, acumulando $-\$6.000$ al cierre del mes).*

---

### B. Proyección Lineal de Liquidez ($f(t) = I_0 - \bar{g} \cdot t$)
* **¿Qué es?**  
  Una función lineal que modela cómo va disminuyendo el dinero disponible día a día a lo largo del mes (30 días).
* **Parámetros del modelo:**
  - **Intercepto $I_0$:** Ingreso inicial recibido a principio de mes ($\$360.000$).
  - **Pendiente negativa $-\bar{g}$:** Gasto medio diario, calculado automáticamente como $\bar{g} = \frac{\sum G}{30}$ ($\$285.000 / 30 = \$9.500/\text{día}$).
  - **Cierre estimado $f(30)$:** Saldo proyectado al llegar al día 30:  
    $$f(30) = 360.000 - 9.500 \cdot 30 = \$75.000$$
  - **Raíz de autonomía máxima ($f(t^*) = 0$):** El día en que el estudiante se quedaría sin un solo peso si continúa con ese ritmo de gasto:  
    $$t^* = \frac{360.000}{9.500} \approx 37,9\text{ días}$$
* **Gráfico SVG:** Dibuja la recta decreciente en tiempo real y marca con puntos interactivos el saldo al día 30 y el punto de quiebre donde se acaba la liquidez.

---

### C. Simulador de Metas de Ahorro: Progresión Aritmética vs. Geométrica
* **¿Qué es?**  
  Un simulador interactivo que le enseña al estudiante el impacto del interés compuesto al ahorrar para una meta (por ejemplo, comprarse un computador o pagar la matrícula).
* **Fórmulas aplicadas:**
  1. **Progresión Aritmética ($a_n$ - Ahorro tradicional / "Bajo el colchón"):**  
     $$a_n = C_0 + n \cdot d$$  
     Donde $C_0$ es el capital inicial y $d$ es el aporte mensual constante. No genera intereses.
  2. **Progresión + Serie Geométrica ($C_n$ - Cuenta de ahorro remunerada / Fondo mutuo):**  
     $$C_n = C_0(1+r)^n + d \cdot \left[ \frac{(1+r)^n - 1}{r} \right]$$  
     Donde $r$ es la tasa de interés mensual efectiva (ej. $0,8\%$, equivalente a un $\sim 10\%$ anual).
* **Interactividad:**  
  En la app puedes cambiar con sliders o escribiendo el capital inicial, el aporte mensual, la tasa y el plazo (en meses). El gráfico SVG dibuja automáticamente ambas curvas para mostrar la ganancia neta por interés ($C_{12} - a_{12} = +\$26.710$).

---

## 🎬 3. Guion rápido para el video / presentación (Qué decir en 2 minutos)

Cuando les toque compartir pantalla y mostrar la aplicación funcionando, pueden usar este relato:

1. *"Aquí podemos ver la aplicación **Summo** desplegada en producción. Para efectos académicos y de evaluación, implementamos un **Modo Simulación** precargado con el caso de estudio de un estudiante universitario con un presupuesto mensual de $\$360.000$."*
2. *"Al ingresar a la vista **Modelo**, la aplicación toma los movimientos y estructura automáticamente la **Matriz de Gastos $M_{4\times 4}$**. Si multiplicamos por el vector unitario, obtenemos el vector de gasto por categoría $\mathbf{g} = M\cdot\mathbf{u}$."*
3. *"Si cambiamos a la pestaña de **Desviación**, el sistema calcula la resta matricial $D = P - M$. Como pueden ver, el software resalta automáticamente en color rojo los sobregiros semanales, como los $-\$6.000$ en Alimentación, permitiendo un control preventivo inmediato."*
4. *"En la parte inferior encontramos la **Función Lineal de Liquidez**, que proyecta un saldo favorable de $\$75.000$ al día 30 y una autonomía total de 37,9 días."*
5. *"Por último, integramos un **Simulador de Ahorro** que compara una Progresión Aritmética frente a una Progresión Geométrica con capitalización mensual, demostrando numéricamente cómo una persona joven puede maximizar su ahorro gracias al interés compuesto."*

---

## ❓ 4. Preguntas típicas que podría hacer el profesor

* **Pregunta:** *¿Por qué usaron una matriz de $4 \times 4$ y no otra dimensión?*  
  **Respuesta:** Porque en la planificación presupuestaria mensual las 4 semanas estándar representan las columnas ($j=1..4$), y agrupamos los egresos en las 4 macrocategorías principales del estudiante (Alimentación, Transporte, Servicios/Estudio y Entretención) como filas ($i=1..4$). Esto permite operaciones matriciales limpias y de fácil interpretación visual.

* **Pregunta:** *¿Qué pasa si el estudiante registra un gasto nuevo en el teléfono?*  
  **Respuesta:** En la app real, el listener reactivo de Google Firebase (`onSnapshot`) detecta el cambio en la base de datos e invoca la función `renderMathModel()`, actualizando en fracciones de segundo la matriz, la pendiente de la recta y los saldos proyectados sin necesidad de recargar la página.
