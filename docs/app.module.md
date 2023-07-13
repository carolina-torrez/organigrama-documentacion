El archivo AppModule se encarga de importar y configurar las dependencias necesarias para la aplicación, como la base de datos y los módulos específicos del organigrama. 
```ts 
import { Module } from '@nestjs/common';
import { MongooseModule } from '@nestjs/mongoose';
import { OrganigramaModule } from './organigrama/organigrama.module';

@Module({ //El decorador @Module() se utiliza para definir un módulo en Nest.js.
  imports: [ //se importa el módulo MongooseModule y se llama a su método forRoot()
    MongooseModule.forRoot('mongodb://127.0.0.1/organigrama'), //Es la URL de conexión a la base de datos MongoDB que se utilizará la aplicacion para almacenar los datos
    OrganigramaModule,
  ],
  Los controladores son responsables de manejar las solicitudes entrantes y los proveedores son responsables de proporcionar instancias de servicios
  controllers: [],
  providers: [],
})
export class AppModule {} //Exporta la clase con las configuraciones necesarias para la aplicacion 
```
