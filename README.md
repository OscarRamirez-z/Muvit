# MUVIT — Sistema de Gestión

Sistema web para gestión de cocinas ocultas: pedidos, inventario, recetas y usuarios.

## Requisitos
- **Python 3.8+** instalado en el sistema
- conexion a internet (solo la primera vez, para descargar lasfuentes de google dsp no es necesario tener internet)

## Cómo iniciar

### Windows
Doble clic en `Iniciar_App.bat`

### Linux / Mac
```bash
chmod +x iniciar_app.sh
./iniciar_app.sh
```

### Manual
```bash
python run.py
```

La app se abre automáticamente en `http://localhost:5000`

## Credenciales por defecto
admin@cocina.com 
admin123

## Tecnologias uasadas
- **Backend**: Python + Flask + SQLite (sin servidor externo)
- **Auth**: JWT (8h) + PBKDF2 (hashing seguro)
- **Frontend**: HTML/CSS/JS puro (SPA)
- **Base de datos**: SQLite (archivo local `instance/cocina.db`)


## Flujo de pedidos
`pendiente` → `en preparacion` → `listo` → `entregado`

- Cocina y Admin avanzan el estado
- Repartidor solo puede marcar `listo` → `entregado`
- Solo Admin puede eliminar pedidos entregados

## Inventario automático
Al agregar un producto a un pedido, el sistema:
1. Verifica stock suficiente de todos los ingredientes
2. Descuenta automáticamente según la receta
3. Registra el movimiento en el historial
