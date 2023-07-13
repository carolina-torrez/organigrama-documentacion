La clase CreateOrganigramaDto representa los datos de entrada al crear un nodo en el organigrama
```ts
import { ApiProperty } from "@nestjs/swagger";

export class CreateOrganigramaDto {//La clase CreateOrganigramaDto, que representa los datos de entrada al crear un nodo en el organigrama.
  name: string;//Esta propiedad es de tipo string y representa el nombre del nodo en el organigrama.

  @ApiProperty({ type: 'string' })//El decorador @ApiProperty({ type: 'string' }) es para especificar que deben ser de tipo string en la documentacion.
  father: string; //Esta propiedad es de tipo string y representa el identificador del nodo padre en el organigrama e indica la relación de jerarquía entre nodos

  @ApiProperty({ type: 'string' })//El decorador @ApiProperty({ type: 'string' }) es para especificar que deben ser de tipo string en la documentacion.
  children: string;//Esta propiedad es de tipo string y representa una lista de identificadores de nodos hijos en el organigrama
}
```