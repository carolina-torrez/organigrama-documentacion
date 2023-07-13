el archivo main sirve para ejecutar el servicio en nestjs establece datos predeterminados en un servicio llamado DataDefaultService, genera la documentación Swagger con la configuración proporcionada y pone en marcha el servidor en el puerto 3000.
```ts
import { NestFactory } from '@nestjs/core'; 
import { AppModule } from './app.module';
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';
import { DataDefaultService } from './organigrama/dafault.data.service'
async function bootstrap() { //Se crea una instancia de la aplicación utilizando NestFactory.     create y pasando como argumento el módulo principal de la aplicación (AppModule)
  const app = await NestFactory.create(AppModule,{cors:true});
  
  const organigrama = app.get(DataDefaultService)//DataDefaultService para establecer datos predeterminados en el organigrama.
  organigrama.setDataDefaultMain() //Esta sentencia inserta los datos del organigrama desde el archivo DataDefaultMain
  
  const config = new DocumentBuilder() // configura los metadatos básicos de la documentación Swagger, como el título, la descripción, la versión y las etiquetas, utilizando la clase DocumentBuilder.
    .setTitle('Cats example') //Establece el título de la documentación
    .setDescription('The cats API description')//Establece la descripción de la API
    .setVersion('1.0')//Establece la versión de la API como "1.0"
    .addTag('organigrama')//Agrega una etiqueta la documentación del "organigrama"
    .build();
  const document = SwaggerModule.createDocument(app, config);// Generan el documento Swagger
  SwaggerModule.setup('api', app, document); //Configuran la interfaz de usuario de Swagger en la ruta '/api' de la aplicación, lista para recibir las solicitudes HTTP.
  
  await app.listen(3000); //El setvicio esta configurado para correr en el puerto 3000
}
bootstrap();
```