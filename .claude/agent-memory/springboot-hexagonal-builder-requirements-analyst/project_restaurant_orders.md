---
name: Proyecto Sistema de Gestión de Órdenes de Restaurante
description: Contexto del proyecto activo — cadena de restaurantes, PRD v1.0 generado en 2026-04-02
type: project
---

El cliente es el dueño de una cadena de restaurantes en crecimiento. El proyecto busca digitalizar la gestión de órdenes, reemplazando procesos manuales y fragmentados.

PRD v1.0 generado y guardado en: `docs/PRD-sistema-gestion-ordenes-restaurante.md`

**Aggregate raíz del dominio:** Orden — con estados: PENDIENTE, EN_PREPARACION, LISTA, ENTREGADA, CANCELADA.

**Actores clave:** Mesero, Cocinero, Cajero, Administrador de Sucursal, Canal Digital Externo, Sistema de Facturación.

**Why:** El sistema resuelve: procesos manuales y fragmentados, retrasos en cocina, errores en entregas, ausencia de trazabilidad, comunicación ineficiente y cierre de cuenta manual.

**How to apply:** Al retomar este proyecto, el PRD es el artefacto de referencia. Los próximos pasos son: validar con el cliente los canales digitales exactos a integrar, el país de operación (normativa fiscal) y el número de sucursales iniciales. Luego pasar al Agente de Diseño.

**Puntos pendientes de validación con el cliente (2026-04-02):**
- Lista exacta de canales digitales a integrar (plataformas de delivery, etc.)
- País de operación para determinar normativa fiscal aplicable
- Número aproximado de sucursales en v1.0
