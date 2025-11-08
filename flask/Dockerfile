#Utilizo la imagen de phyton slim debido a que es liviana y estable.
FROM python:3.11-slim 

ENV PYTHONUNBUFFERED=1
ENV POETRY_VIRTUALENVS_CREATE=false

WORKDIR /app

# Instalo las dependencias necesarias
COPY . .

RUN pip install --no-cache-dir -r requirements.txt
#no-cache-dir para evitar que se guarden archivos temporales de la instalación

ENV PORT=6969
#puerto en el que correrá la aplicación, si no, por defecto utilizará 6969 ya que en el run.py está definido así por defecto.
EXPOSE 6969

CMD ["gunicorn", "--bind", "0.0.0.0:6969", "app:app", "--workers", "3", "--access-logfile", "-", "--error-logfile", "-"]
