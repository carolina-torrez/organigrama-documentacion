La clase UpdateOrganigramaDto representa los datos de entrada al actualizar un nodo existente en el organigrama.
```ts
import { PartialType } from '@nestjs/swagger';//La importacion se utiliza para generar una versión parcial de un DTO existente
import { CreateOrganigramaDto } from './create-organigrama.dto';//Se importa la clase CreateOrganigramaDto desde el archivo './create-organigrama.dto'. Esto se hace para definir UpdateOrganigramaDto como una versión parcial de CreateOrganigramaDto

export class UpdateOrganigramaDto extends PartialType(CreateOrganigramaDto) {//La clase UpdateOrganigramaDto implica que solo se deben proporcionar las propiedades que se desean actualizar 
  father?: string;//Esta propiedad representa el identificador del nodo padre al que se desea actualizar el nodo existente en el organigrama.
}
```