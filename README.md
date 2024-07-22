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


## JSON CONSULTAR DATOS RUT
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



 


