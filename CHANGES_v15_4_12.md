# PhysioSentinel AI v15.4.12 · Explicit Horizon Probability UI

Base: v15.4.11 Horizon-Calibrated Probability.

## Cambio funcional de interfaz

- El bloque **«Probabilidad calibrada de evolución favorable a X días»** contiene ahora un selector visible de horizonte temporal con **3, 7, 14 y 30 días**.
- El horizonte seleccionado se reutiliza directamente para todas las predicciones Nivel 1 + Nivel 2 de la pestaña 10.
- El mismo bloque muestra, para el paciente y fase seleccionados:
  - Horizonte solicitado.
  - Probabilidad calibrada de evolución favorable (%), cuando el modelo probabilístico está validado.
  - Soporte temporal aprendido (p10–p90, mediana y rango observado).
  - Clasificación del horizonte como soporte principal, soporte limitado o extrapolación fuera del rango observado.
  - Estado/nivel de calibración contextualizado con Brier Test, mejora frente a prevalencia y AUC Test.
- Se aclara expresamente que «probabilidad favorable a X días» significa estado fisiológico esperado **en ese horizonte**, no mantenimiento continuo de una tendencia durante X días.

## Sin cambios en el motor

- No se modifica el XGBRegressor residual del Nivel 2.
- No se modifica XGBClassifier de probabilidad favorable.
- Se conserva Train/Validation/Test 70/15/15, calibración Platt, Test final intocable, Walk-Forward y criterio de promoción.
- Se conserva la selección inteligente de características y el aprendizaje multivariado cruzado.
- No se fuerza reentrenamiento ni se invalidan modelos activos compatibles.
