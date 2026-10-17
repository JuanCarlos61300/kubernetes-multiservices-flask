#imagen oficial de Python
FROM python:3.11-slim
#directorio de trabajo
WORKDIR /app
#archivos de la aplicación al contenedor
COPY . /app
# Instala las dependencias
RUN pip install --no-cache-dir -r requirements.txt
# Expone el puerto 80
EXPOSE 80
# Ejecuta la aplicación
CMD ["python", "app.py"]
