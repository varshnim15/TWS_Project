# TWS_Project
Docker FlaskApp
Flask App
ubuntu@ip-172-31-12-224:~/docker_project/flask_app$ ls
Dockerfile  app.py  dockerfile  requirements.txt  static  templates

vim Dockerfile
# Use the official Python image from the Docker Hub
FROM python:3.11-slim
# Set the working directory in the container
WORKDIR /app
# Copy the current directory contents into the container at /app
COPY . /app
# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt
# Make port 5000 available to the world outside this container
EXPOSE 5000
# Define environment variable
ENV FLASK_APP=app.py
# Run app.py when the container launches
CMD ["flask", "run", "--host=0.0.0.0"]
                                                                                                                 
**ubuntu@ip-172-31-12-224:~$ sudo docker images**
REPOSITORY   TAG         IMAGE ID       CREATED          SIZE
flask-app    latest      acffea04309e   36 minutes ago   145MB
<none>       <none>      cecd43378df5   38 minutes ago   130MB
mysql        latest      7ce93a845a8a   5 days ago       586MB
python       3.11-slim   13d803497f98   2 weeks ago      130MB
nginx        latest      a72860cb95fd   5 weeks ago      188MB

**ubuntu@ip-172-31-12-224:~$ sudo docker ps**
CONTAINER ID   IMAGE              COMMAND                  CREATED         STATUS         PORTS                                       NAMES
b459c98e47a5   flask-app:latest   "flask run --host=0.…"   8 minutes ago   Up 8 minutes   0.0.0.0:5000->5000/tcp, :::5000->5000/tcp   compassionate_lumiere
63e8c81c7146   nginx:latest       "/docker-entrypoint.…"   2 hours ago     Up 2 hours     0.0.0.0:80->80/tcp, :::80->80/tcp           agitated_meninsky
bf2717299bc0   mysql:latest       "docker-entrypoint.s…"   2 hours ago     Up 2 hours     3306/tcp, 33060/tcp                         exciting_lamport

ubuntu@ip-172-31-12-224:~/docker_project/flask_app$ sudo docker stop 8478ad24c131 && sudo docker remove 8478ad24c131
ubuntu@ip-172-31-12-224:~/docker_project/flask_app$ sudo docker run -d -p 5000:5000 flask-app:latest
change security group to anywhere for 5000 port
take public key of instance and add 5000 port and check on browser 
http://3.137.214.156:5000/ 
 


