# PhysioSentinel AI v15.4.11 · Horizon-Calibrated Probability

- Añade `horizonte_dias` como variable explícita en cada transición longitudinal.
- Nivel 1 proyecta al horizonte solicitado cuando las fechas están disponibles.
- Nivel 2 XGBoost residual mantiene selección inteligente, 70/15/15, Test final intocable y Walk-Forward.
- Nueva capa `XGBClassifier` para **P(evolución favorable a X días)**, donde Favorable = Δ compuesto > +3 puntos.
- Calibración de probabilidad mediante Platt scaling entrenada **solo en Validation (15%)**.
- El Test final (15%) se usa una única vez para Brier/log-loss/AUC. La app solo etiqueta el porcentaje como probabilidad calibrada si el Brier Test mejora frente al baseline de prevalencia aprendido en Train.
- La interfaz permite seleccionar 1–365 días y muestra soporte temporal observado (p10–p90 y rango completo).
- Fuera del rango observado se marca explícitamente como extrapolación; dentro de colas p10/p90 se marca soporte limitado.
- Se mantiene la trazabilidad de familias, importancia XGBoost, históricos, PostgreSQL, Lazy Sync y exportaciones existentes.

**Interpretación:** la probabilidad es fisiológica/modelística para el criterio Δ compuesto > +3, no probabilidad de diagnóstico, evento clínico o desenlace médico.
