# Embat — Producto, posicionamiento y modelo

> Notas de research. Verificar/actualizar con la web si el caso aporta datos
> distintos. Fuente principal: embat.io y cobertura pública (TechCrunch,
> rankings).
>
> **Cómo usar este archivo:** sirve para entrar en contexto y formular mejores
> preguntas. NO es prueba de nada durante el caso:

| Tipo de información | Cómo utilizarla |
| ------------------- | --------------- |
| Capacidad públicamente documentada | Contexto para preguntar ("¿esto aplica a este cliente/bancos?") |
| Claim comercial de Embat | No asumir que aplica a todos los clientes ni a este caso |
| Inferencia propia | Hipótesis a validar |
| Información desconocida | Preguntar durante el caso |

Los claims comerciales están marcados con **[claim]**.

## De un vistazo

- **Qué es:** TMS cloud-native (SaaS) que centraliza tesorería: conecta bancos,
  ERPs y pasarelas de pago en una sola plataforma.
- **Fundación:** 2021, Madrid, por Antonio Berga, Carlos Serrano (ex-JPMorgan)
  y Tomás Gil.
- **Financiación:** ~$16M Series A (2024, Creandum) y €30M Series B (2026).
- **Clientes (referencias públicas):** Playtomic, Cabify, Wallapop, Fever;
  ~150 clientes corporativos en Europa (2024).
- **ICP:** mid-market europeo (grupos multi-entidad, multi-banco, multi-divisa),
  equipos de finanzas de pocas personas. No enterprise puro (Kyriba) ni SMB
  puro (Agicap).
- **Certificaciones:** ISO 27001, SOC 2, GDPR.

## Módulos del producto

### 1. Connectivity Hub
- **Bank Connectivity:** conexión en tiempo real vía APIs (PSD2/corporate),
  H2H, EBICS, SWIFT, EDITRAN. **[claim]** 15.000+ instituciones financieras.
  **[claim]** Event-driven (cada ~15 min), no batch nocturno.
- **ERP Connectivity:** integración **bidireccional** con SAP, Microsoft
  Dynamics, Oracle NetSuite, Sage, Workday, DATEV, Holded, Zoho… (20+ sistemas).
  Vía APIs, conectores nativos o file-based (SFTP).
  - Datos AP/AR y facturas entran de ERP → Embat.
  - Asientos, estados de pago y resultados de conciliación vuelven al ERP.
  - **[claim]** Despliegue estándar 2–3 semanas; custom 4–6 semanas.

### 2. Treasury Management
- **Cashflow Management & Forecasting:** posición consolidada multi-banco,
  multi-entidad, multi-divisa; forecasting adaptativo; categorización
  automática (TellMe AI, **[claim]** precisión 90%+ en 3 niveles: reglas → IA →
  revisión manual); scenario planning y alertas.
- **Intercompany Operations:** deuda e intereses intercompany, liquidaciones y
  asientos automáticos, matching por reglas.
- **Risk Management:** riesgo de contrapartida, cartera de deuda, detección IA,
  controles de términos y límites.

### 3. Cash Accounting & Reconciliation
- **Bank Reconciliation:** matching IA entre bancos, PSPs y ERP; excepciones
  marcadas; asientos publicados automáticamente.
- **PSP Reconciliation:** Stripe, Adyen, PayPal y otros; comisiones,
  chargebacks y liquidaciones.

### 4. Corporate Payments
- **Payment Flows & Execution:** lotes de pago centralizados (AP, nóminas,
  impuestos, ad-hoc, internacionales) en +50 divisas; validación previa (IBAN,
  formato, campos); ficheros por banco (**pain.001**, MT101, MT103) vía API
  corporativa, H2H, EBICS, SWIFT o EDITRAN.
- **Approval Flows:** reglas por importe, entidad, tipo; aprobación
  desktop/móvil; banner si cambia un beneficiario; una autenticación para
  todos los bancos.
- **FX y pagos internacionales:** cuenta global complementaria, clearing local,
  costes FX visibles, asientos automáticos de conversión.

### 5. IA — TellMe
Agente de tesorería: categorización, detección de anomalías, sugerencias de
forecast, comentarios de reporting. (Partner de Google Cloud Vertex AI desde
2023.)

## Diferenciadores que suele destacar Embat (todos: verificar, no asumir)

1. Conectividad real-time API-first con cobertura de bancos regionales europeos.
2. Integración ERP bidireccional con conectores nativos.
3. Conciliación IA (banco + PSP + ERP).
4. Modular: activar solo lo necesario.
5. Velocidad de despliegue (semanas) vs. TMS tradicionales (meses).
6. Multi-entidad/multi-divisa nativo para grupos mid-market.
7. Seguridad enterprise (ISO 27001, SOC 2) a precio mid-market.

## Pricing

- Modular, por módulo, sin precios públicos; venta asistida/demo.

## Competencia declarada

En deals (fuentes públicas): Agicap, Atlar, Kyriba, Nomentia, TIS, Coupa, FIS,
HighRadius, Rho, Serrala, Trovata, SAP. (Ver `research/competitors.md`.)

## Preguntas a validar con el equipo de producto (durante el caso)

- ¿Qué parte de las conexiones bancarias es API y cuál file-based (EBICS,
  SWIFT, SFTP)?
- ¿Qué nivel de visibilidad tiene Embat sobre el estado real de un pago tras
  enviarlo? ¿Qué estados y motivos de rechazo llegan por cada canal
  (pain.002, camt.054, extractos)?
- ¿Qué capacidades funcionan igual para todos los bancos y cuáles dependen de
  cada integración? ¿Latencia/frecuencia por banco?
- ¿Qué limitaciones actuales generan más trabajo manual a los clientes?
- ¿Qué módulos están más maduros y cuáles son prioritarios en el roadmap?
- ¿Cuánto volumen procesan los clientes y qué % de pagos falla o requiere
  intervención?

## Oportunidades de pregunta en el caso

- ¿El caso toca un módulo concreto (pagos, conciliación, forecasting) o la
  plataforma completa?
- ¿Aprovecha una capacidad existente (TellMe, conectividad, ERP) o requiere
  construir nueva?
- ¿El problema es de calidad de datos, de flujo de aprobación, de cobertura
  bancaria o de experiencia multi-entidad?
