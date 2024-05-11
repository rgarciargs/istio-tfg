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

## Ejecución
Para generar una plantilla en tu entorno de Kubernetes en el modo Stable, sigue los pasos siguientes asumiendo que tienes el binario 'kustomize' accesible desde el mismo directorio:
```bash
kustomize build stable
```
Puedes consultar el resultado de la plantilla generada en el fichero `examples/template_stable_example.yaml`

Para generar una plantilla en tu entorno de Kubernetes en el modo Mirror, sigue los pasos siguientes asumiendo que tienes el binario 'kustomize' accesible desde el mismo directorio:
```bash
kustomize build mirror
```
Puedes consultar el resultado de la plantilla generada en el fichero `examples/template_mirror_example.yaml`

