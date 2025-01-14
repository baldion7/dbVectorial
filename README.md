# Sistema de Búsqueda Empresarial

Un sistema de búsqueda semántica construido con ChromaDB y modelos Transformer para gestionar y buscar documentos empresariales. Este sistema proporciona capacidades avanzadas de gestión de documentos con funcionalidad de búsqueda semántica utilizando técnicas modernas de PLN.

## Características

- Búsqueda semántica de documentos utilizando embeddings basados en transformers
- Gestión de documentos (agregar, actualizar, eliminar)
- Filtrado por categorías
- Puntuación de similitud
- Gestión de metadatos
- Capacidades de búsqueda basada en vectores

## Requisitos

```
chromadb
transformers
torch
scikit-learn
```

## Instalación

1. Crear un entorno virtual (recomendado):
```bash
python -m venv venv
source venv/bin/activate  # En Windows usar: venv\Scripts\activate
```

2. Instalar los paquetes requeridos:
```bash
pip install chromadb transformers torch scikit-learn
```

## Uso

### Uso Básico

```python
from enterprise_search import initialize_chromadb, initialize_transformer_model, add_company_data

# Inicializar el sistema
collection = initialize_chromadb()
tokenizer, model = initialize_transformer_model()

# Agregar datos iniciales de la empresa
add_company_data(collection, tokenizer, model)

# Realizar una búsqueda
results = search_documents(collection, "¿Cuáles son los horarios de trabajo?", tokenizer, model)
```

### Funciones Principales

1. **Búsqueda de Documentos**
```python
results = search_documents(collection, "tu consulta aquí", tokenizer, model, n_results=2)
```

2. **Filtrado por Categoría**
```python
results = filter_by_category(collection, "products_services")
```

3. **Actualizar Documentos**
```python
update_document(collection, tokenizer, model, 
               doc_id="doc_id",
               new_text="nuevo contenido", 
               new_metadata={"category": "ejemplo"})
```

4. **Eliminar Documentos**
```python
delete_document(collection, "doc_id")
```

## Aprendizajes

Este código demuestra varios conceptos importantes en la recuperación de información moderna y PLN:

1. **Embeddings Vectoriales**: Aprende cómo convertir texto en representaciones numéricas usando modelos transformer.
2. **Búsqueda Semántica**: Comprensión de cómo implementar búsquedas basadas en similitud más allá de la simple coincidencia de palabras clave.
3. **Gestión de Documentos**: Implementación práctica de operaciones CRUD en una base de datos vectorial.
4. **Integración de Machine Learning**: Trabajo con modelos pre-entrenados y su incorporación en un sistema más grande.
5. **Operaciones de Base de Datos**: Uso de ChromaDB para almacenamiento y recuperación de vectores.
6. **Métricas de Similitud**: Implementación de medidas de similitud coseno y distancia vectorial.

## Arquitectura

El sistema utiliza:
- ChromaDB para almacenamiento y recuperación de vectores
- Sentence Transformers (all-MiniLM-L6-v2) para generar embeddings
- TF-IDF y similitud coseno para puntuación adicional de relevancia
- Metadatos estructurados para categorización de documentos

## Mejores Prácticas

1. Siempre inicializar el modelo y la colección al inicio de la aplicación
2. Usar metadatos apropiados para categorizar los documentos
3. Considerar el procesamiento por lotes para grandes conjuntos de documentos
4. Implementar manejo de errores para uso en producción
5. Monitorear el uso de memoria al trabajar con grandes colecciones de documentos
6. Considerar actualizar los embeddings periódicamente si el contenido del documento cambia

## Limitaciones

- El sistema carga el modelo transformer en memoria, lo que requiere RAM adecuada
- La longitud del documento está limitada por la longitud máxima de secuencia del modelo transformer
- El rendimiento de búsqueda puede degradarse con colecciones muy grandes de documentos

## Contribuciones

¡Siéntete libre de enviar problemas y solicitudes de mejora!
