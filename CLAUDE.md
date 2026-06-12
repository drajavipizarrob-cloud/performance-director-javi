# Performance Director — Contexto del proyecto

## Qué es este proyecto
PWA de un solo archivo (index.html) que funciona como coach de rehabilitación conversacional. No es un dashboard. Es un chat con un Performance Director de élite como interfaz principal.

## Atleta
- Mujer, 34 años, nadadadora recreativa en rehabilitación de hombro izquierdo
- TDAH: alto riesgo de sobreentrenamiento cuando los síntomas mejoran
- Trabajo remoto, sedentarismo prolongado
- Objetivo: volver a nadar con mecánica escapular correcta, sin recaídas

## Regla no negociable — Integridad de datos
NUNCA fabricar métricas. Si no hay dato real registrado, el campo NO se muestra.
- Dolor, energía, sueño, estrés: son valores DIARIOS, no persistentes. No mostrar valores de días anteriores como si fueran actuales.
- Readiness (Verde/Amarillo/Rojo): solo aparece si fue declarado en la conversación actual.
- Tendencias y gráficos: solo con 5+ entradas reales en el log.

## Arquitectura
- Un solo archivo: index.html
- Sin build, sin framework, sin dependencias externas
- localStorage para persistencia local (sessionLog, conversationHistory, athlete-phase)
- API: Google Gemini (gemini-3.5-flash con fallback a gemini-2.5-flash)
- Deploy: GitHub Pages

## Modelo de datos actual
- sessionLog: array de {type, content, date}. type puede ser 'training', 'symptom', 'active-break'
- conversationHistory: array de {role, content}
- athlete-phase: string (ej. 'Fase 2 (Rebuilding)')

## Próximas features priorizadas
1. Rediseño visual del briefing (ver mockup adjunto en conversación)
2. Check-in diario estructurado: dolor (0-10), energía (0-10), sueño (horas), estrés (0-10)
3. Los tiles de check-in muestran valores de HOY si existen, o botón de captura si no
4. Captura estructurada guarda campos numéricos separados en localStorage
5. Fila de adherencia semanal (días con registro sobre 7, dato real)
6. Flare-risk warning automático basado en datos reales del log

## Estado clínico — Diagnósticos confirmados (RMN, junio 2026)
1. **Bursitis subacromiosubdeltoidea leve** (mild subacromiosubdeltoid bursitis)
2. **Edema óseo AC leve por sobrecarga**, contorno regular — NO artropatía
3. **Edema focal en vientre acromial del deltoides**, distal — mecanismo en investigación (posible tracción-hiperflexión)
4. **Infraespinoso Goutallier grado 1** — infiltración grasa mínima, sin impacto funcional en esta etapa

**Etiología confirmada:** probable SIRVA (Shoulder Injury Related to Vaccine Administration). Vacunación ~1 mes atrás, inyección probablemente alta/lateral en deltoides → irritación de bursa subacromial → hombro sensibilizado → mecanismo tracción-hiperflexión superpuesto. Sin patología estructural previa. Pronóstico: resolución completa esperada con manejo conservador actual.

**Integridad estructural confirmada (RMN):**
- Tendones del manguito rotador: grosor normal, sin rotura
- Tendón del bíceps: normal, sin tenosinovitis
- Labrum: íntegro, sin rotura
- Articulación glenohumeral: congruente, sin derrame, cartílago normal
- Sin edema capsular ni obliteración del intervalo

## Restricciones clínicas activas (confirmadas por imagen)
- Sin overhead bajo carga (bursitis subacromial)
- Sin fondos/dips, sin colgarse, sin aducción cruzada bajo carga (edema AC)
- El estiramiento deltoides cruzado con tracción horizontal forzada está PERMANENTEMENTE eliminado
- Braceo compacto al correr, sin cruzar la línea media
- Dolor articular punzante = detener ejercicio inmediatamente

## Fase actual registrada
Fase 2 — Rebuilding (criterios: dolor 2-4/10, síntomas estables, función diaria mejorada)
Criterios de progresión a Fase 3: dolor 0-2/10 sostenido + función diaria completa + rehab sin dolor
