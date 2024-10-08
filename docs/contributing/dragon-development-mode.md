# dRAGon Development Mode

{% hint style="warning" %}
**VISUAL STUDIO CODE DEV CONTAINERS**

In order to be as close as possible to the development environment, we **strongly** recommend using Visual Studio Code Dev Containers. You can find the configuration file in the `.devcontainer` folder.

If it's not possible please make sure you have the following tools installed with the **correct** versions:

* Java 17
* Gradle 8.7
* Node.js 20
* NPM 10
* "Unix like" System (Linux, MacOS)

However we do **NOT** accept any issues related to troubles encountered by **NOT** using the Dev Containers.
{% endhint %}

## Clone Repository

```shell
git clone https://github.com/dRAGon-Okinawa/dRAGon
```

## Prepare Dependencies

```shell
gradle pnpmInstall build
```

## Launching dRAGon

### Backend + Frontend

```shell
# Launch full dRAGon app :
gradle bootRun

# Open your browser at http://localhost:1985 to access the dRAGon app
```

### Backend Only

```shell
# Launch only the Backend API server and the Job Server :
gradle bootRun -x :frontend:pnpmBuild -x :backend:copyWebApp

# Open your browser at http://localhost:1985/api/swagger-ui.html to access the Backend API server

# To continuously build your changes, open a new terminal :
gradle backend:bootJar -continuous -xtest -x :frontend:pnpmBuild -x :backend:copyWebApp
```

### Frontend Only

```shell
# Go to the frontend directory
cd frontend

# 1. Launch the frontend
# 1.1. Inside one terminal launch the Frontend
pnpm dev

# 1.2. Open your browser at http://localhost:9527 to access the Frontend

# 2. To use the Frontend you need to launch the Backend or the Mock API server
# 2.A. Launch the Mockoon API server inside another terminal
npx @mockoon/cli start --data mockoon_dRAGon.json

# OR

# 2.B. Launch the Backend (Only) inside another terminal
# See the (Backend Only) section above
```

