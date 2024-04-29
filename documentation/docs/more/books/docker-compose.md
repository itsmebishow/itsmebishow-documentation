## `Django` with `MySql`

If you choose `Docker Compose` to deploy your Django web application along with a MySQL database, you would typically follow these steps:

- `Dockerfile` for Django App:

  Here's a basic example of what a Dockerfile for a Django application might look like:

  ```
  FROM python:3.9

  WORKDIR /app

  COPY requirements.txt /app/
  RUN pip install --no-cache-dir -r requirements.txt

  COPY . /app/

  CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
  ```

- `docker-compose.yml`:

  Below is an example `docker-compose.yml` file for a Django app with a MySQL database:

  ```
    version: '3'

    services:
    db:
        image: mysql:5.7
        restart: always
        environment:
        MYSQL_DATABASE: 'mydatabase'
        MYSQL_USER: 'myuser'
        MYSQL_PASSWORD: 'mypassword'
        MYSQL_ROOT_PASSWORD: 'rootpassword'
        ports:
        - '3306:3306'

    web:
        build: .
        command: python manage.py runserver 0.0.0.0:8000
        volumes:
        - .:/app
        ports:
        - '8000:8000'
        depends_on:
        - db
  ```

- Django `Settings`:

  Make sure your Django application's settings are configured to use the MySQL database. You'll need to update the `DATABASES` setting in your Django `settings.py` file to point to the MySQL database container

- Run `Docker Compose`:

  Run docker-compose up in the directory containing your docker-compose.yml file. This command will start the containers defined in the docker-compose.yml file. Docker Compose will build the Docker images (if necessary) and start the containers for your Django app and MySQL database.

- `Access` Your Application:

  Once Docker Compose has started the containers, you should be able to access your Django application by navigating to `http://localhost:8000` in your web browser.
