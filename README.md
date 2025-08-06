# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
   npx expo start
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

## Get a fresh project

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.




npx expo start --port 3000
npm run reset-proyect
npm install nativewind tailwindcss react-native-reanimated react-native-safe-area-context
npx tailwindcss init
npx expo customize metro.config.js

https://www.youtube.com/watch?v=f8Z9JyB2EIE&t=2008s







## Propósito
Este repositorio es simplemente para utilizar como base al momento de construir una app con react usando Docker de la manera más simple.

# Paso 0
Instalar Docker Desktop. Vea referencia <a href=#docker>#1</a>.

# Paso 1
Una vez Docker Dektop instalado queremos levanatar un contenedor en base de node para luego tratarlo como un 'mini virtual machine' donde instalaremos las dependencias necesarias utilizando npm. 

Para este proyecto decidí utilizar la imagen de node:20-bullseye. Sin embargo, puede elegir, en Docker Hub, la imagen base que prefiera, pero deberá tomar en cuenta que algunas dependencias pudieran estar sujetas a su imagen. Vea referencia <a href='#docker-hub'>#2</a>.

Para levantar el contendor en base a la imagen seleccionada debemos correr el siguiente comando:

<strong>SUSTITUYA TODOS LOS TERMINOS <ASI> POR LOS DE SU PREFERENCIA.</strong>

<code>docker run -d -v <nombre_del_volumen>:/app -p <3000:3000> --name <nombre_del_contenedor> node:20-bullseye tail -f /dev/null. </code>

# Explicación
- <code>docker run</code> levanta un contenedor basado en la imagen que se le especifique.
- <code>-d</code> mantiene corriento el contenedor en segundo plano.
- <code>-v <nombre_del_volumen>:/app</code> crea un volumen de docker para poder preservar los datos del contenedor en la máquina local. Este contenedor es accesible atraves de la carpeta de volumes con el nombre <nombre_del_volumen>. Dentro del contenedor la carpeta <code>app</code> será exactamente igual a la del volumen.
- <code>-p <3000:3000></code> mapea el puerto del contenedor con el de tu máquina. En el futuro se configurará react para que utilice el puerto 3000 (o el que usted elija), en ese punto el puerto 3000 de nuestra máquina local reflejará lo mismo que el puerto 3000 del contenedor. Siempre recomendable que ambos puertos sean iguales.
- <code>--name <nombre_del_contenedor></code> le asigna un nombre al contenedor.
- <code>node:20-bullseye</code> imagen base (puede elegir cualquier otra).
- <code>tail -f /dev/null</code> permite mantener el contenedor corriendo aunque no haya nada sucediendo dentro de él.


# Paso 2
Una vez creado el contenedor, debemos entrar para trabajar en él.

<code>docker exec -it <nombre_del_contenedor> bash</code>

Esto nos permitirá entrar al contenedor utilizando un terminal bash.



# Paso 3
Verificar la versión de <code>node</code> que vive dentro del contenedor utilizando el siguiente comando.

<code>node -v</code>

En el caso de usar la imagen <code>node:20-bullseye</code>, el output debe ser <code>v20.19.4</code>. Si elige otra imagen esta version puede cambiar.





# Paso 4
Iniciar proyecto de react. Para este proyecto crearé una aplicación utilizando <code>React Native</code> para que sea escalable para IOS, Android y Web. Dentro del contenedor:
- <code>cd app</code>
- <code>npx create-expo-app@latest <nombre_del_proyecto></code> ver referencia <aa href='#react-expo'>#3</a>. Puede ser requerido instalar algunas otras dependencias como <code>Expo</code> si el output del comando lo requiere.

# Paso 5
Ejecutar la aplicación base que se crea con el último comando. Para necesitamos:
- <code>cd <nombre_del_proyecto></code>
- <code>npx expo start --dev-client --port 3000</code>

En este punto ya tienes un contenedor de Docker que permite desarrollar una aplicación con React Native. Si quisieras seguir aprendiendo de React Native puedes ver la referencia <a href='react-tutorial'></a>



## Referencias
1. <a id='docker' href='https://docs.docker.com/desktop/setup/install/windows-install/'>Docker Desktop</a>
2. <a id='docker-hub' href='https://hub.docker.com/_/node/tags'>Docker Hub</a>
3. <a id='react-expo' href='https://react.dev/learn/creating-a-react-app'>React-Expo</a>
3. <a id='react-tutorial' href='https://docs.expo.dev/tutorial/create-your-first-app/'>React-Expo-Tutorial</a>