Carpeta de desarrollo para adaptar el DIOT para instancias con legacy.
Tiene el objetivo de obtener todos sus datos directamente del tax JSON, alojado en todas las facturas de proveedor (vendor bills). 
Para en dado momento, considerar la posibilidad de normalizar un solo código para ambas instancias, y que tanto suitetax como legacy puedan usar el tax JSON.

##DOCUMENTACIÓN DE ERRORES#
Se incluyó y activó el tax JSON en la instancia de VNA para poder usarlo, simplemente estaba desactivado para vendor bills en su custrecord. 
Es necesario ponerle el tipo de operación y el tipo de tercero a todos los proveedores, pues es una funcionalidad nueva incluida con el DIOT, una instancia sin el diot no tiene estos dos campos 
previamente llenados
Se desactivaron todas las limitaciones con un if (suitetax==false)
Se creó una nueva función para sacar los objetos con el taxJSON, usando como base el que ya se tenía, pero usando la función json.PARSE
Se tienen errores con todas las columnas relacionadas con el taxDetails, pues es una función exclusiva de suitetax.
