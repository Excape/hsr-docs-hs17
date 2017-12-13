# Service Contracts & Microservices

## Einschub SOAP
- Ursprünglich Simple Object Access Protocol, aber jetzt nur noch als Eigenname definiert
- XML-Format, was den "Wunsch" des Service Requestors an den Provider beschreibt
- In jedem Body Entry ist ein Schema definiert, das den "Contract" bildet
- Unterscheiden von RPC! Ist konzeptionell nur ein "Intent" etwas zu machen, nicht direkt ein Call
- Alles geht über POST (Kritik von REST-Leuten)

## WSDL
- XML-Schema für Service Contracts
- Definiert auch Datenschema, was in REST lange nicht gemacht wurde
- REST kann auch mit WSDL 2.0 beschrieben werden, hat sich aber nicht durgesetzt gegen RESTful HTTP

## Microservices
- Vorher "fine-grained SOA"
- Jede Komponente ist ein Service, der separat deployed werden kann (aber nicht muss)
- Jeder Service kann unterschiedlichen Storage / Programmiersprache verwenden
- So kann separat skaliert werden, z.B. nur den Katalog eines Online-Shops rauf skalieren bei Black Friday
- Nach Fowler ein eigener Architektur-Stil (O. Zimmermann disagrees)
- Aus DDD: Jedes Aggregate kann ein Microservice sein

## Resources
- <https://www.subbu.org/blog/2008/09/on-linking-part-2>