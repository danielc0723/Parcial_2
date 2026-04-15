parcial_cafeteria_sabana/
│
├── parcial_corte_2_solucion.ipynb        # Notebook principal con toda la solución
│
├── parcial_2_productos_sucios.csv        # Datos originales sucios - Productos
├── parcial_2_clientes_sucios.csv         # Datos originales sucios - Clientes
├── parcial_2_proveedores_sucios.csv      # Datos originales sucios - Proveedores
│
├── parcial_2_productos_limpios.csv       # Datos normalizados - Productos
├── parcial_2_clientes_limpios.csv        # Datos normalizados - Clientes
├── parcial_2_proveedores_limpios.csv     # Datos normalizados - Proveedores
│
├── parcial_2_cafeteria.db                # Base de datos SQLite final (4 tablas)
│
└── README.md                             # Este archivo
```
---

`sql
CREATE TABLE ventas (
    id_venta      INTEGER PRIMARY KEY AUTOINCREMENT,
    id_cliente    INTEGER NOT NULL,
    id_producto   INTEGER NOT NULL,
    id_proveedor  INTEGER NOT NULL,
    cantidad      INTEGER NOT NULL,
    total_venta   REAL    NOT NULL,
    fecha_venta   TEXT    NOT NULL,
    FOREIGN KEY (id_cliente)   REFERENCES clientes(id_cliente),
    FOREIGN KEY (id_producto)  REFERENCES productos(id_producto),
    FOREIGN KEY (id_proveedor) REFERENCES proveedores(nit_proveedor)
);
```


```
┌──────────────┐       ┌─────────────┐       ┌───────────────┐
│   clientes   │       │   ventas    │       │   productos   │
│─────────────│       │────────────│       │──────────────│
│ id_cliente PK│──────►│ id_cliente  │◄──────│ id_producto PK│
│ nombre_cliente│      │ id_producto │       │ nombre_producto│
│ tipo_cliente │       │ id_proveedor│       │ categoria     │
│ email        │       │ cantidad    │       │ precio        │
│ telefono     │       │ total_venta │       │ stock         │
│ fecha_nac.   │       │ fecha_venta │       │ fecha_venc.   │
└──────────────┘       └─────────────┘       └───────────────┘
                              │
                              ▼
                       ┌──────────────┐
                       │  proveedores │
                       │─────────────│
                       │ nit_prov. PK │
                       │ nombre_empresa│
                       │ ciudad       │
                       │ contacto     │
                       │ telefono     │
                       │ email        │
                       └──────────────┘
