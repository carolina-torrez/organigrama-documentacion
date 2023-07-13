La clase CreateFatherDto representa los datos de entrada al agregar un padre a un nodo existente en el organigrama.
```ts
import { ApiProperty } from "@nestjs/swagger";//Este decorador se utiliza para especificar las propiedades de un DTO en la documentación del Swagger

export class CreateFatherDto {//Esta propiedad representa el identificador del nodo padre que se desea agregar al nodo existente en el organigrama.
  @ApiProperty({ type: 'string' }) //Esta propiedad representa el identificador del nodo padre que se desea agregar al nodo existente en el organigrama
  father: string;//father, que representa el identificador del nodo padre que se desea agregar.
}
```