# Caso de Estudio: Phishing con suplantación de Google y dominio gubernamental falsificado

Fecha del análisis: 7 de agosto de 2026

Autor: SpainCheck Pro (Sebastian Bish Adell)

Categoría: OSINT / Análisis de amenazas / Phishing

## Resumen

Análisis forense completo de una campaña de phishing recibida por correo electrónico, que simula un aviso de bloqueo de cuenta de Google con amenaza de borrado de fotos y vídeos. El caso combina técnicas de suplantación de identidad, typosquatting de un dominio gubernamental (.gov) y abuso de infraestructura legítima de Google Cloud Storage para alojar el contenido malicioso.

## Hallazgos clave

- Remitente falsificado: dominio sin registro real, usado solo para el envío.

- Typosquatting gubernamental: la ruta de envío del correo simula un dominio oficial estadounidense (.commerce.gov), enrutado en realidad a través de un dominio en India.

- Suplantación universitaria: la dirección de respuesta imita un dominio de una universidad real de Estados Unidos.

- Abuso de Google Cloud Storage: el enlace malicioso se aloja en un bucket público de almacenamiento de Google, una técnica que dificulta el bloqueo automático porque el dominio raíz es legítimo.

- Infraestructura activa en Italia: el dominio de typosquatting resuelve a una IP de un proveedor de hosting italiano, registrado hace poco más de un año con privacidad WHOIS activada.

## Metodología

El análisis se dividió en dos fases:

1. Análisis de cabeceras de correo: identificación de remitente real, ruta de envío, y dirección de respuesta falsificada.

2. Reconocimiento pasivo en Kali Linux: verificación de WHOIS de los cuatro dominios implicados, geolocalización de la IP asociada, búsqueda de certificados TLS relacionados en registros de Transparencia de Certificados, y comprobación del estado en vivo del enlace malicioso.

Todo el reconocimiento se realizó de forma pasiva, sin interactuar directamente con la infraestructura del atacante más allá de una verificación HTTP de solo cabeceras.

## Resultado

El informe completo, con el detalle técnico de cabeceras, cadena de infraestructura, resultados de WHOIS, DNS, Transparencia de Certificados y verificación HTTP del enlace, está disponible en el PDF adjunto en esta carpeta.

El incidente fue reportado a INCIBE-CERT junto con el correo original en formato de archivo y este informe técnico como anexo.

## Descargo de responsabilidad

Este análisis se realiza con fines exclusivamente defensivos y educativos, siguiendo metodología OSINT pasiva. No se ha interactuado con los sistemas del atacante más allá de lo necesario para confirmar el estado del enlace.
