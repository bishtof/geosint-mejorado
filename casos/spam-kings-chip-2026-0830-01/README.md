# Caso de Estudio: Spam de casino "King's Chip" con suplantacion del encabezado "De:"

**Fecha del analisis:** 30-31 de agosto de 2026

**Autor:** SpainCheck Pro (Sebastian Bish Adell)

**Categoria:** OSINT / Analisis de amenazas / Spam y spoofing de dominio

## Resumen

Analisis forense de un correo no solicitado que promociona una plataforma de casino online ("King's Chip", remitente mostrado como "First-Time-Player-Rewards"), clasificado automaticamente como spam por Gmail, que ademas advirtio de un posible intento de suplantacion de la propia direccion del destinatario. Las cabeceras de autenticacion (SPF/DKIM/DMARC) muestran inconsistencias compatibles con spoofing del encabezado "De:". No se ha observado en el contenido disponible una solicitud directa de credenciales bancarias o contrasenas: se trata de publicidad de iGaming no solicitada con indicios de suplantacion de dominio, mas que de phishing dirigido de robo de credenciales.

## Hallazgos clave

Dominio remitente decorativo: 3pcine.5jyud6.4krfst.us, un subdominio anidado alfanumerico bajo un dominio base .us de bajo coste, patron habitual en infraestructura de envio masivo desechable.

Fallo de autenticacion: DKIM y DMARC en FAIL; el PASS de SPF corresponde al dominio de envelope-from (Return-Path), no al "De:" visible, confirmando indicios de spoofing del encabezado.

Aviso propio de Gmail: el mensaje fue marcado como posible respuesta automatica simulando haberse enviado desde la propia direccion del destinatario.

Evidencia pendiente de verificacion: esta version del informe (v2, revisada) retira una seccion previa (v1) de "cadena de transito" (cabeceras Received) que no pudo corroborarse y que incluia una referencia a infraestructura de ElevenLabs sin relacion alguna con el envio del correo. Los resultados de WHOIS/DNS sobre 4krfst.us y la IP 198.50.125.247 quedan pendientes de ejecucion directa por el analista.

## Metodologia

El analisis se dividio en dos fases:

Fase 1 (analisis de capturas de Gmail): identificacion de remitente mostrado, destinatario, resultados resumidos de autenticacion (SPF/DKIM/DMARC) y aviso de suplantacion propio de Gmail.

Fase 2 (reconocimiento pasivo con herramientas de Kali Linux, pendiente/en curso): comandos preparados de whois, dig, dnsenum, amass y sublist3r sobre el dominio raiz 4krfst.us y la IP de origen, para confirmar de forma independiente los datos de registro, DNS y organizacion del bloque IP antes de darlos por verificados.

Todo el reconocimiento se ha planteado de forma pasiva, sin interactuar con los enlaces del mensaje.

## Resultado

El informe tecnico completo, con el detalle de datos del mensaje, autenticacion de correo, infraestructura del dominio remitente y evaluacion, esta disponible en el PDF adjunto en esta carpeta (informe-caso-3pcine-4krfst-v2-revisado.pdf).

El caso puede notificarse a INCIBE-CERT (CERT nacional de referencia en Espana) a traves de su formulario web, por correo a incidencias@incibe-cert.es, o por la linea 017, adjuntando el .eml original como evidencia primaria.

## Descargo de responsabilidad

Este analisis se realiza con fines exclusivamente defensivos y educativos, siguiendo metodologia OSINT pasiva. No se ha interactuado con los enlaces ni con la infraestructura del remitente mas alla de la revision de las cabeceras disponibles en Gmail. Los datos del destinatario han sido anonimizados en todo el documento.
