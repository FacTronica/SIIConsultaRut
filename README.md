# SII Consulta Rut
Api para obtener datos de un rut registrado en el sii chile.   
El objetivo de esta api es entregar la información necesaria para automatizar el proceso de facturación electrónica con software propio.

## CARACTERÍSTICAS:

**Compatibilidad:** Windows, Linux y Mac.

**Integración:** ApiRest Datos Json.

**Código Abierto:** Al comprar la API Servidor Se entrega el código fuente.

## Documentación

A continuación se detalla el procedimiento a seguir para realizar la integración.

-   [01.-Enviar Petición Json]
-   [02.-Recuperar respuesta Json]
-   [03.-Interpretar Respuesta Json] 


## EJEMPLO PHP: JSON CONSULTAR DATOS RUT (json_datos.php)
````
<?php
$datos_consultarut = array(
"TOKEN" => "AQUI-VA-SU-TOKEN-ACCESO",
"RUT"=>"11111111-1",
"X509Certificate"=>"-----BEGIN CERTIFICATE-----
MIIGWDCCBUCgAwIBAgIIBavbb0GKlm0wDQYJKoZIhvcNAQELBQAwga8xCzAJBgNV
BAYTAkNMMRQwEgYDVQQKDAtFLVNpZ24gUy5BLjE5MDcGA1UECwwwVGVybXMgb2Yg
TSmxX4TuS1L05xGe5AaEJYri2gI0SfdevQh4eDMYGrzNYqBJIvtj67b93XuNuEDQ
v8041jGr0dX6tnlc3HM3X0jJihBnfRniTGoT1/crb+hG9wVNpdIUvNSgQCE=
-----END CERTIFICATE-----",
"PrivKey"=>"-----BEGIN PRIVATE KEY-----
MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQC2K6IZnrVXQ/Jr
vQ/Qw2ZK9ZvsarV9rw7S+ZcCNbTgvWpuIQvQ3OHyU1OboVVcG9K2cMoNVFzjPBDf
AyAS29BVf7YVAwddGlLstlnwbzj9knFEmgj3jSOi/zPKGQhq9x778GhjTNf5jotg
mdydCXvmsa8ZQR6HkWI24rfzgQDYdRvBwJQ9bnbS/QKBgDNGnzIo0Uo/l67bP/Hw
RfhXCTR/lGBk7AeYHOp3dyYe442tfdbwheZrxTgudkXzVQKlFNi0XNiGZHq8jGJZ
abQRtkLYJAyrRDuLKEUS8dN7nTeLlsGC8hRgL8qYulvcp8daOGPQCploQ4GZTyTO
JnqDfIrSPYshHU4o57fJ7vzG
-----END PRIVATE KEY-----"
);
?>
````

## EJEMPLO PHP: ENVIAR JSON (json_envia.php)
````
<?php
function JsonEnviar($arregloJson,$url){
    $payload = json_encode($arregloJson);
    $curl = curl_init($url);
    curl_setopt($curl, CURLOPT_HEADER, false);
    curl_setopt($curl, CURLOPT_PORT,443);
    curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($curl, CURLOPT_HTTPHEADER,array("Content-type: application/json"));
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS,$payload);
    $json_response = curl_exec($curl);
    $status = curl_getinfo($curl, CURLINFO_HTTP_CODE);
    curl_close($curl);
    return $json_response;
}
?>
````

## EJEMPLO PHP: ENVIAR JSON Y CAPTURAR RESPUESTA
````
<?php
include("json_envia.php");
include("json_datos.php");
$url_api="url-end-point";
$retorno=JsonEnviar($arregloJson,$url_api);
$jsonArray  = json_decode($retorno,true);
echo "<pre>";
var_dump($jsonArray);
echo "</pre>";
?>
````
 
## EJEMPLO : RESPUESTA FORMATO ARRAY
````
array(6) {
  [0]=>
  array(7) {
    ["Rut"]=>
    string(10) "77777777-7"
    ["RazonSocial"]=>
    string(14) "EMPRESA PRUEBA"
    ["Consulta"]=>
    string(16) "22-07-2024 11:13"
    ["TieneActividades"]=>
    string(2) "SI"
    ["FechaInicio"]=>
    string(10) "05-04-2016"
    ["MonedaExtranjera"]=>
    string(2) "NO"
    ["MenorTamano"]=>
    string(2) "SI"
  }
  [1]=>
  array(3) {
    [1]=>
    array(5) {
      ["Actividad"]=>
      string(70) "VENTA AL POR MENOR DE COMPUTADORES, EQUIPO PERIFERICO, PROGRAMAS INFOR"
      ["Codigo"]=>
      string(6) "474100"
      ["Categoria"]=>
      string(7) "Primera"
      ["AfectaIva"]=>
      string(2) "Si"
      ["Fecha"]=>
      string(10) "05-04-2016"
    }
    [2]=>
    array(5) {
      ["Actividad"]=>
      string(70) "ACTIVIDADES DE CONSULTORIA DE INFORMATICA Y DE GESTION DE INSTALACIONE"
      ["Codigo"]=>
      string(6) "620200"
      ["Categoria"]=>
      string(7) "Primera"
      ["AfectaIva"]=>
      string(2) "Si"
      ["Fecha"]=>
      string(10) "05-04-2016"
    }
    [3]=>
    array(5) {
      ["Actividad"]=>
      string(32) "OTROS TIPOS DE ENSEÑANZA N.C.P."
      ["Codigo"]=>
      string(6) "854909"
      ["Categoria"]=>
      string(7) "Primera"
      ["AfectaIva"]=>
      string(2) "No"
      ["Fecha"]=>
      string(10) "09-04-2021"
    }
  }
  [2]=>
  array(7) {
    [1]=>
    array(2) {
      ["Documento"]=>
      string(19) "Factura Electronica"
      ["UltimoTimbraje"]=>
      string(4) "2020"
    }
    [2]=>
    array(2) {
      ["Documento"]=>
      string(38) "Factura No Afecta O Exenta Electronica"
      ["UltimoTimbraje"]=>
      string(4) "2023"
    }
    [3]=>
    array(2) {
      ["Documento"]=>
      string(18) "Boleta Electronica"
      ["UltimoTimbraje"]=>
      string(4) "2022"
    }
    [4]=>
    array(2) {
      ["Documento"]=>
      string(25) "Boleta Exenta Electronica"
      ["UltimoTimbraje"]=>
      string(4) "2022"
    }
    [5]=>
    array(2) {
      ["Documento"]=>
      string(23) "Nota Debito Electronica"
      ["UltimoTimbraje"]=>
      string(4) "2016"
    }
    [6]=>
    array(2) {
      ["Documento"]=>
      string(24) "Nota Credito Electronica"
      ["UltimoTimbraje"]=>
      string(4) "2022"
    }
    [7]=>
    array(2) {
      ["Documento"]=>
      string(31) "Boleta De Terceros Electronicas"
      ["UltimoTimbraje"]=>
      string(4) "2024"
    }
  }
  [3]=>
  array(9) {
    ["rut"]=>
    string(8) "77777777"
    ["dv"]=>
    string(1) "7"
    ["fecha"]=>
    string(10) "2019-06-11"
    ["calle"]=>
    string(12) "ALAMEDA 340"
    ["numero"]=>
    string(3) "199"
    ["bloque"]=>
    string(0) ""
    ["departamento"]=>
    string(2) "62"
    ["villapoblacion"]=>
    string(0) ""
    ["comuna"]=>
    string(11) "PROVIDENCIA"
  }
  [4]=>
  array(5) {
    ["razon_social"]=>
    string(14) "EMPRESA PRUEBA SPA"
    ["num_resolucion"]=>
    string(2) "80"
    ["fecha_resolucion"]=>
    string(10) "22-08-2014"
    ["email"]=>
    string(39) "intercambio@gmail.com"
    ["url"]=>
    string(17) "www.website.cl"
  }
  [5]=>
  array(1) {
    ["nombre"]=>
    NULL
  }
}
````
