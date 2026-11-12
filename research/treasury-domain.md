# Glosario de dominio — Tesorería, pagos e integraciones

> Terminología para hablar con propiedad durante el caso.

## Tesorería (TMS)

- **TMS (Treasury Management System):** plataforma que conecta bancos, ERPs y
  sistemas de pago para automatizar cash visibility, forecasting, pagos y
  conciliación.
- **Cash position / positioning:** posición de caja consolidada en tiempo real
  por banco, entidad, cuenta y divisa.
- **Cash flow forecasting:** proyección de flujos futuros a partir de datos
  históricos (pagos reales) y confirmados (facturas, nóminas, impuestos).
- **Banking pool:** agrupación de cuentas/saldos para gestionar liquidez
  global (reports por entidad, divisa, fecha).
- **Cash pooling / netting:** centralización física o nocional de saldos;
  netting intercompany: compensación de deudas internas para reducir
  movimientos reales.
- **Month-end close:** cierre contable mensual: conciliar bancos, publicar
  asientos, cerrar libros. Fricción clásica que Embat ataca.

## Pagos

- **Payment batch:** lote de pagos (proveedores, nóminas, impuestos) preparado,
  aprobado y ejecutado en conjunto.
- **Approval workflow / maker-checker:** reglas de aprobación por importe,
  entidad o tipo; separación de quien prepara y quien firma; trazabilidad
  total (audit trail).
- **Four-eyes / dual control:** toda operación requiere dos personas
  (compliance típico en tesorería).
- **Payment run:** ejecución periódica de lotes de pago.

## Formatos y protocolos

- **ISO 20022:** estándar de mensajería financiera. Claves:
  - **pain.001:** instrucción de pago (iniciación).
  - **pain.002:** acuse de estado del pago.
  - **camt.053:** extracto bancario (movimientos del día).
  - **camt.052:** saldos/actividad intradía.
  - **camt.054:** notificación de abonos/cargos.
- **MT101 / MT103:** mensajes SWIFT legacy: instrucción de pago (MT101) y
  transferencia individual (MT103).
- **SEPA:** zona única de pagos en euros (transferencias, débitos directos).
- **EBICS:** protocolo estándar europeo para intercambio de ficheros con
  bancos (común en Alemania/Francia/España).
- **H2H (host-to-host):** conexión directa entre el sistema del cliente y el
  banco, sin portal ni ficheros manuales.
- **API corporativa / PSD2 API:** conexión en tiempo real vía APIs bancarias
  (open banking).
- **SWIFT:** red global de mensajería interbancaria; también canal de
  transmisión de ficheros (FileAct).
- **EDITRAN:** protocolo de transmisión de ficheros bancarios (común en España).

> **No confundir mensajes con garantías:** recibir un `pain.002`, `camt.053` o
> `camt.054` NO implica disponer siempre de una causa de rechazo accionable.
> Depende del banco, del canal y de la información que realmente proporcione:
> algunos devuelven solo "rechazado" sin código de motivo, y la latencia varía
> por entidad. Preguntar siempre qué estado/motivo llega por cada banco antes
> de asumir normalización completa.

## Conceptos operativos (para pagos y conectividad)

- **Payment lifecycle:** ciclo de un pago: creado → validado → aprobado →
  enviado → aceptado/rechazado por el banco → ejecutado → confirmado.
- **Payment status vs. settlement confirmation:** un pago puede estar
  "aceptado por el banco" y no haberse liquidado aún (settlement) — y un
  extracto (camt.053) confirma la liquidación días después.
- **Idempotency:** reintentar una instrucción sin duplicar el pago. Crítico
  cuando hay reintentos tras fallos de red/tiempo de espera.
- **Straight-through processing (STP):** % de pagos procesados de extremo a
  extremo sin intervención manual.
- **Data freshness:** antigüedad del último dato disponible (saldos, estados);
  clave cuando la conectividad no es tiempo real.
- **Bank connectivity coverage:** qué instituciones/cuentas están conectadas y
  por qué canal; cobertura ≠ calidad del dato.
- **Reconciliation exceptions:** movimientos sin pareja que requieren revisión
  humana (el flujo de excepciones es parte del producto, no un caso raro).
- **False positives / false negatives:** en detección de anomalías y matching:
  alertas de más erosionan confianza; de menos, riesgo no detectado.

## Conectividad ERP

- **Integración bidireccional:** AP/AR y facturas fluyen del ERP a la
  plataforma; asientos, estados de pago y conciliación vuelven al ERP.
- **Journal entry / asiento:** registro contable publicado en el ERP (GL).
- **GL (General Ledger):** libro mayor contable.
- **Event-driven sync:** sincronización en tiempo real (minutos) en lugar de
  batch nocturno.
- **AP/AR:** Accounts Payable (proveedores) / Accounts Receivable (clientes).

## Conciliación

- **Bank reconciliation:** casar movimientos bancarios con registros contables
  (facturas, pagos, cobros).
- **PSP reconciliation:** conciliar liquidaciones de pasarelas de pago
  (Stripe, Adyen, PayPal): comisiones, chargebacks, fees, netting.
- **Matching:** emparejamiento de transacciones; reglas deterministas → IA →
  revisión manual (modelo de 3 niveles de Embat).
- **Exceptions / mismatches:** transacciones sin pareja que requieren revisión
  humana.

## Riesgo y FX

- **FX accounting:** contabilización automática de conversiones: fees, spreads,
  ganancias/pérdidas realizadas y no realizadas.
- **Counterparty risk:** riesgo de crédito con contrapartes (clientes, bancos,
  deudores).
- **Hedging:** cobertura de riesgo de divisa o tipo de interés.

## Perfiles de usuario

- **CFO:** decisor estratégico; ve cash position, forecasting y reporting.
- **Treasurer / Finance Manager:** gestiona liquidez, banking pool, deuda,
  riesgos.
- **Accountant / Contable:** ejecuta conciliación, cierres, asientos.
- **AP/AR specialist:** prepara y ejecuta lotes de pago/cobro.

## Fricciones típicas de tesorería (para enmarcar problemas)

1. Manualidad: exportar/importar ficheros entre ERP y portales bancarios.
2. Falta de visibilidad: posiciones consolidadas solo a cierre de día.
3. Conciliación lenta: matching manual de movimientos.
4. Fraude/error: cambios de beneficiario sin control, dobles pagos.
5. Multi-banco/multi-entidad: fragmentación de procesos y aprobaciones.
6. Cierres largos: mes de trabajo manual para cerrar libros.
