# istio-tfg

# Plantillas de Kustomize para Itzuli con Istio

## Descripción
Este repositorio contiene las plantillas de Kustomize para la configuración y el despliegue del traductor neuronal de euskera, Itzuli, optimizado con Istio en un entorno Kubernetes. Estas configuraciones están diseñadas para facilitar la gestión y el despliegue de los servicios en diferentes entornos, utilizando las capacidades de Istio para mejorar la observabilidad, el enrutamiento y la seguridad.

## Estructura del Repositorio
La estructura del repositorio se organiza de la siguiente manera:
- `bases/`: Contiene los manifiestos base de Kubernetes y Istio.
  - `t.yaml`: Define los servicios y configuraciones de Itzuli.
  - `vs.yaml`: Configuraciones de VirtualService para el enrutamiento de Istio.
  - `se.yaml`: ServiceEntry para la gestión de entradas externas.
  - `gw.yaml`: Gateway que define los puntos de entrada para el tráfico.
  - `kustomization.yaml`: Archivo de Kustomize para organizar la aplicación de todos los manifiestos.
- `stable/`: Contiene los manifiestos para aplicar los patches para la configuración del modo Stable
  - `dr.yaml`: Define el DestinationRule para las configuraciones 'stable'.
  - `vs.yaml`: Configuraciones de VirtualService para el enrutamiento de Istio.
  - `kustomization.yaml`: Archivo de Kustomize para organizar la aplicación de todos los manifiestos.
- `mirror/`: Contiene los manifiestos para aplicar los patches para la configuración del modo Mirror
  - `dr.yaml`: Define el DestinationRule para las configuraciones 'stable' y 'rc'.
  - `vs.yaml`: Configuraciones de VirtualService para el enrutamiento de Istio.
  - `kustomization.yaml`: Archivo de Kustomize para organizar la aplicación de todos los manifiestos.

## Pre-requisitos
- Kubernetes v1.19+
- Kustomize v4.0.5+
- Istio instalado en el cluster de Kubernetes
- Pipeline de Jenkins parametrizado

## Advertencia

Este repositorio se ha realizado con fines didácticos para un Trabajo de Fin de Grado. En un entorno real como el de de itzuli, existen una serie de herramientas donde se parametrizan los modelos de traducción, por lo que si quieres utilizar este código, deberás adaptarlo a tus necesidades.

## Ejecución
Para generar una plantilla en tu entorno de Kubernetes en el modo Stable, sigue los pasos siguientes asumiendo que tienes el binario 'kustomize' accesible desde el mismo directorio:
```bash
kustomize build stable
```
Puedes consultar el resultado de la plantilla generada en el fichero `examples/kustomize-examples/template_stable_example.yaml` , asumiendo una parametrización correcta del modelo adm-eu-es de Itzuli.

Para generar una plantilla en tu entorno de Kubernetes en el modo Mirror, sigue los pasos siguientes asumiendo que tienes el binario 'kustomize' accesible desde el mismo directorio:
```bash
kustomize build mirror
```
Puedes consultar el resultado de la plantilla generada en el fichero `examples/kustomize-examples/template_mirror_example.yaml` , asumiendo una parametrización correcta del modelo adm-eu-es de Itzuli.

## Objetos de Istio generados
Si quieres ver un ejemplo de los objetos de Istio generados (Gateway, ServiceEntry, VirtualService y DestinationRule) para el modelo adm-eu-es en modo Mirror, puedes consultar el directorio `examples/istio-objects` 

