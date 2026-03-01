📊 ANÁLISIS DE CHURN - TELECOMUNICACIONES
Descripción del Proyecto
Análisis completo de cancelación de clientes (churn) para una empresa de telecomunicaciones, incluyendo preprocesamiento de datos, análisis exploratorio y preparación para modelado predictivo.

🔍 Etapas del Análisis
1. Carga y Verificación
Carga exitosa de datos JSON desde repositorio

Verificación de estructura válida

2. Transformación de Variables
One-hot encoding de variables categóricas

Conversión a formato numérico para ML

3. Análisis de Balance de Clases
73% clientes activos (No Churn)

27% clientes que cancelaron (Yes Churn)

Ratio de desbalance: 3:1 (requiere técnicas de balanceo)

4. Técnicas de Balanceo Evaluadas
Undersampling | Oversampling | SMOTE ✅ | SMOTE+Tomek

5. Normalización/Estandarización
Variables con escalas muy diferentes (tenure: 1-72, cargos: $18-$8,500)

Modelos sensibles (KNN, SVM, RL): requieren escalado

Modelos no sensibles (Random Forest, XGBoost): no requieren

6. Correlaciones con Churn
🔴 Aumentan Churn	🟢 Disminuyen Churn
Contrato mensual (+0.40)	Antigüedad (-0.35)
Fibra óptica (+0.30)	Contrato 2 años (-0.30)
Pago electrónico (+0.25)	Contrato 1 año (-0.20)
Cargos mensuales altos (+0.20)	Servicio DSL (-0.15)
7. Hallazgos Clave
📌 Tiempo de contrato:

Clientes que cancelan: 10 meses promedio

Clientes activos: 38 meses promedio

Mayor riesgo: primeros 6 meses (>40% churn)

📌 Gasto total:

Relación no lineal con churn

Canceladores: menor gasto total (menos tiempo)

Pero tienen cargos mensuales más altos

📌 Combinaciones de alto riesgo:

Contrato mensual + Fibra óptica + Pago electrónico

📈 Recomendaciones para Modelado
Features prioritarias:
customer.tenure (antigüedad)

account.Contract_Month-to-month

internet.InternetService_Fiber optic

account.PaymentMethod_Electronic check

account.Charges.Monthly

Features derivadas sugeridas:
python
df['high_risk_combo'] = (contrato_mensual & fibra_optica)
df['avg_monthly_charge'] = gasto_total / antiguedad
df['is_new_customer'] = antiguedad < 6
Modelos recomendados:
Random Forest o XGBoost (no requieren escalado)

Aplicar SMOTE solo en entrenamiento

Evaluar con F1-score y AUC-ROC

💼 Implicaciones de Negocio
Segmento	Riesgo	Estrategia
Clientes nuevos (<6 meses)	🔴 Alto	Programa onboarding, descuentos iniciales
Contrato mensual + Fibra	🔴 Alto	Ofrecer contrato anual con beneficio
Clientes 1-2 años	🟢 Bajo	Programas fidelización
Pago electrónico	🟡 Medio	Incentivar pago automático
✅ Conclusión
Análisis integral que prepara datos para modelado predictivo de churn, identificando patrones críticos y proporcionando bases sólidas para estrategias de retención proactivas.
