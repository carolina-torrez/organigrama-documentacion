El codigo OrganigramaController es responsable de manejar las solicitudes HTTP relacionadas con el organigrama y llamar al OrganigramaService correspondiente para realizar las operaciones necesarias. Se importan varios decoradores y clases necesarios para definir y configurar el controlador y otras clases y DTOs relacionados con el organigrama.
```ts
import { Controller, Get, Post, Body, Param, Put } from '@nestjs/common';
import { OrganigramaService } from './organigrama.service';
import { NodoOrganigrama } from './schema/organigrama.schema';
import { ApiTags } from '@nestjs/swagger';
import { CreateOrganigramaDto } from './dto/create-organigrama.dto';
import { UpdateOrganigramaDto } from './dto/update-organigrama.dto';
import { CreateNewEntityDto } from './dto/create-unidad';
import { CreateFatherDto } from './dto/set-father.dto';
import { CreateChildrenDto } from './dto/set-son.dto';

//Se utiliza el decorador @ApiTags('organigrama') para asignar una etiqueta al controlador en la documentación Swagger y se utiliza el decorador @Controller('organigrama') para establecer la ruta base del controlador como 'organigrama'
@ApiTags('organigrama')
@Controller('organigrama')
export class OrganigramaController {
  constructor(private readonly organigramaService: OrganigramaService) {} //

  @Get()//El decorador @Get() se utiliza para asignar una ruta HTTP GET al método obtenerOrganigrama() y obtener el organigrama mediante el metodo this.organigramaService.obtenerOrganigrama()
  async obtenerOrganigrama() {
    return await this.organigramaService.obtenerOrganigrama();
  }
  @Get('/enlazados')//El decorador @Get('/enlazados') define una ruta de tipo GET para obtener el organigrama con los nodos enlazados 
  async obtenerOrganigramaUnidos() {
    return await this.organigramaService.obtenerOrganigramaEnlazados();
  }

  @Get(':id') //El decorador @Get(':id') define una ruta de tipo GET que acepta un parámetro id en la URL para obtener un nodo específico 
  async obtenerNodo(@Param('id') id: string) {
    return this.organigramaService.obtenerNodo(id);
  }

  @Post()//El decorador @Post() define una ruta de tipo POST para crear un nuevo nodo en el organigrama. Los datos del nodo se pasan en el cuerpo de la solicitud
  async crearNodo(@Body() nodo: CreateNewEntityDto) {
    return this.organigramaService.crearNodo(nodo);
  }

  @Put(':id/hijo-padre')// El decorador @Put llama al método agregarHijoPadres(id, hijo) del servicio organigramaService para agregar el hijo o el padre al nodo especificado
  async agregarHijoPadre(@Param('id') id: string, @Body() hijo: UpdateOrganigramaDto) {
    return this.organigramaService.agregarHijoPadres(id, hijo);
  }

  @Put(':id/padre')//El decorador @Put llama al método agregarfather(id, hijo) del servicio organigramaService para agregar el padre al nodo que no tiene padre
  async agregarPadre(@Param('id') id: string, @Body() hijo: CreateFatherDto) {
    return this.organigramaService.agregarfather(id, hijo);
  }
  
  @Put(':id/hijo') //El decorador @Put llama al método agregarSon(id, hijo) del servicio organigramaService para agregar un hijo al un nodo en especifico
  async agregarHijo(@Param('id') id: string, @Body() hijo: CreateChildrenDto) {
    return this.organigramaService.agregarSon(id, hijo);
  }
}
```