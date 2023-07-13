 la clase CreateNewEntityDto representa los datos de entrada al crear una nueva entidad en el organigrama
```ts
import { ApiProperty } from "@nestjs/swagger";//Este decorador se utiliza para especificar las propiedades de un DTO en la documentación del Swagger.

export class CreateNewEntityDto {//Esta clase representa los datos de entrada al crear una nueva entidad en el organigrama.
  @ApiProperty({ required: true })//Este decorador se utiliza para especificar que esta propiedad es requerida en la documentación generada por Swagger y la Api no puede estar vacia
  name: string;//Esta propiedad representa el nombre de la entidad que se desea crear.
}
```