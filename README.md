Carpeta de desarrollo para adaptar el DIOT para instancias con legacy.
Tiene el objetivo de obtener todos sus datos directamente del tax JSON, alojado en todas las facturas de proveedor (vendor bills). 
Para en dado momento, considerar la posibilidad de normalizar un solo código para ambas instancias, y que tanto suitetax como legacy puedan usar el tax JSON.



##CONFIGURACIONES NECESARIAS EN INSTANCIAS CON LEGACY##
--Es necesario ponerle el tipo de operación y el tipo de tercero a todos los proveedores, pues es una funcionalidad nueva incluida con el DIOT, una instancia sin el diot no tiene estos dos campos 
previamente llenados
--Es necesario configurar todos los códigos de impuesto (tax codes) en el campo DIOT-TIPO DE IMPUESTO 
--Es necesario activar el standard vendor form en todas las bills y configurar el tipo de operacion
--Es necesario activar el tax JSON en el standard vendor form 
--Es necesario hacer un deploy del script correspondiente a taxJSON (comunmente EFX_FE_Tax_Fields) en journal entry y vendor bill


##DOCUMENTACIÓN#
Se incluyó y activó el tax JSON en la instancia de VNA para poder usarlo, simplemente estaba desactivado para vendor bills en su custrecord. 
Se desactivaron todas las limitaciones con un if (suitetax==false)
Se creó una nueva función para sacar los objetos con el taxJSON, usando como base el que ya se tenía, pero usando la función json.PARSE
Para cumplir el objetivo del taxJSON , se creó una búsqueda que lo extrae, luego se obtienen los resultados y se les aplica un JSON.parse, para sacar los valores numéricos que se necesitan
Se tuvieron errores con todas las búsquedas que incluyen el campo "taxDetails", se usó una búsqueda que regresa solo el taxJSON y se usan sus valores para sustituir los que regresa el taxDetails. 