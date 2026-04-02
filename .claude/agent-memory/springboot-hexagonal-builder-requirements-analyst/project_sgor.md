---
name: Proyecto SGOR - Sistema de Gestión de Órdenes de Restaurante
description: Contexto, decisiones y estado del proyecto SGOR analizado en sesión de requerimientos
type: project
---

Sistema de Gestión de Órdenes de Restaurante (SGOR) para cadena de restaurantes en crecimiento.

**Problema:** Procesos manuales y fragmentados generan retrasos en cocina, errores en entregas y ausencia de trazabilidad.

**Objetivos core (Must Have):**
- Centralización de pedidos (mesas físicas + canal digital)
- Comunicación en tiempo real a cocina (KDS)
- Trazabilidad de estados de órdenes (PENDIENTE > EN_PREPARACION > LISTA > ENTREGADA > CERRADA)
- Cierre de cuenta con facturación vinculada a la orden

**Actores identificados:** Mesero, Cliente Digital, Cocinero/KDS, Administrador, Cajero, Sistema de Pagos externo.

**Aggregates definidos:** Orden (raíz principal), Producto de Menú, Mesa, Pago.

**Regla de negocio crítica:** El precio del ítem se congela al momento del registro de la Orden — cambios en el menú no afectan órdenes ya creadas.

**Riesgo abierto:** Facturación electrónica requiere clarificación de jurisdicción antes de diseñar el módulo de Comprobante.

**PRD generado en:** docs/prd/PRD-sistema-gestion-ordenes-restaurante.md
**SRS generado en:** docs/srs/ (generado por skill srs-document-builder)

**Why:** El cliente es dueño de una cadena en crecimiento que opera con procesos manuales; la digitalización es urgente para la operación en hora punta.

**How to apply:** Este es el proyecto activo del repositorio. Toda referencia a "el sistema" o "el restaurante" apunta a SGOR v1.
