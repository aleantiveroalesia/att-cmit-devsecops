# AT&T CMIT DevSecOps Automation

[![Build Status](https://github.com/att-cmit/devsecops-automation/actions/workflows/ci.yml/badge.svg)](https://github.com/att-cmit/devsecops-automation/actions/workflows/ci.yml)
[![Security Scan](https://github.com/att-cmit/devsecops-automation/actions/workflows/security.yml/badge.svg)](https://github.com/att-cmit/devsecops-automation/actions/workflows/security.yml)
[![Code Coverage](https://codecov.io/gh/att-cmit/devsecops-automation/branch/main/graph/badge.svg)](https://codecov.io/gh/att-cmit/devsecops-automation)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/github/v/release/att-cmit/devsecops-automation)](https://github.com/att-cmit/devsecops-automation/releases)

## 📋 Descripción

Prueba

Sistema de automatización DevSecOps para el equipo CMIT (Core Management and Infrastructure Technology) de AT&T. Este proyecto integra seguridad en cada fase del ciclo de desarrollo, desde el código hasta la producción, implementando las mejores prácticas de la industria.

### 🎯 Objetivos Principales

- **Shift-Left Security**: Integrar controles de seguridad desde las primeras fases del desarrollo
- **Automatización Continua**: Eliminar procesos manuales propensos a errores
- **Visibilidad Total**: Métricas y monitoreo en tiempo real del pipeline
- **Compliance**: Cumplimiento automático con regulaciones SOX, PCI-DSS y estándares internos

## 🏗️ Arquitectura del Sistema

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   GitHub    │───▶│   Actions   │───▶│   ArgoCD    │───▶│ Kubernetes  │
│ Source Code │    │   CI/CD     │    │   GitOps    │    │ Production  │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
       │                    │                    │                    │
       ▼                    ▼                    ▼                    ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  Security   │    │  Testing &  │    │ Deployment  │    │ Monitoring  │
│  Scanning   │    │  Quality    │    │ Automation  │    │ & Alerting  │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
```

### 🔧 Stack Tecnológico

- **Version Control**: Git + GitHub Enterprise
- **CI/CD**: GitHub Actions + Self-hosted Runners
- **Security**: SonarQube, Snyk, Aqua Security, TruffleHog
- **Infrastructure**: Kubernetes, Terraform, Helm
- **Monitoring**: Prometheus, Grafana, Datadog
- **GitOps**: ArgoCD, Flux

## 🚀 Quick Start

### Prerrequisitos

Asegúrate de tener instalado:

```bash
# Herramientas básicas
- Git >= 2.34.0
- Node.js >= 18.0.0
- Docker >= 20.10.0
- kubectl >= 1.25.0

# Herramientas de desarrollo
- VS Code con extensiones recomendadas
- Pre-commit hooks
- AWS CLI (para deployments)
```

### Instalación y Setup

```bash
# 1. Clonar el repositorio
git clone https://github.com/att-cmit/devsecops-automation.git
cd devsecops-automation

# 2. Instalar dependencias
npm install

# 3. Configurar pre-commit hooks
pre-commit install

# 4. Copiar configuración de desarrollo
cp .env.example .env.local

# 5. Levantar entorno de desarrollo
docker-compose up -d

# 6. Ejecutar tests para verificar setup
npm test
```

## 📦 Estructura del Proyecto

```
att-cmit-devsecops/
├── .github/                    # GitHub workflows y templates
│   ├── workflows/
│   │   ├── ci.yml             # Continuous Integration
│   │   ├── security.yml       # Security scanning
│   │   ├── deploy.yml         # Deployment automation
│   │   └── release.yml        # Release management
│   ├── ISSUE_TEMPLATE/        # Templates para issues
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── CODEOWNERS            # Code review assignments
├── docs/                      # Documentación del proyecto
│   ├── architecture.md       # Arquitectura del sistema
│   ├── deployment.md         # Guías de deployment
│   ├── security.md          # Políticas de seguridad
│   └── api/                 # Documentación de APIs
├── src/                      # Código fuente principal
│   ├── api/                 # APIs y servicios
│   ├── web/                 # Frontend applications
│   ├── workers/             # Background jobs
│   └── shared/              # Código compartido
├── tests/                    # Test suites
│   ├── unit/               # Unit tests
│   ├── integration/        # Integration tests
│   ├── e2e/               # End-to-end tests
│   └── security/          # Security tests
├── infrastructure/           # Infrastructure as Code
│   ├── terraform/          # Terraform configurations
│   ├── kubernetes/         # K8s manifests
│   ├── helm/              # Helm charts
│   └── monitoring/        # Monitoring configs
├── scripts/                 # Automation scripts
│   ├── setup.sh          # Environment setup
│   ├── deploy.sh         # Deployment script
│   ├── security-scan.sh  # Security scanning
│   └── backup.sh         # Backup procedures
├── .gitignore              # Git ignore rules
├── .pre-commit-config.yaml # Pre-commit configuration
├── docker-compose.yml     # Local development environment
├── Dockerfile             # Container definition
├── package.json           # Node.js dependencies
├── README.md             # This file
├── SECURITY.md           # Security policy
├── LICENSE               # Project license
└── CHANGELOG.md          # Release notes
```

## 🧪 Testing y Calidad

### Comandos de Testing

```bash
# Unit tests
npm run test

# Integration tests
npm run test:integration

# End-to-end tests
npm run test:e2e

# Security tests
npm run test:security

# Coverage report
npm run test:coverage

# Performance tests
npm run test:performance
```

### Quality Gates

El proyecto mantiene los siguientes estándares de calidad:

- ✅ **Code Coverage**: Mínimo 85%
- ✅ **Security Scan**: 0 vulnerabilidades críticas
- ✅ **Code Quality**: Grado A en SonarQube
- ✅ **Performance**: Response time <200ms
- ✅ **Dependencies**: 0 vulnerabilidades conocidas

## 📊 Métricas DORA

### Estado Actual vs Objetivos

| Métrica | Estado Actual | Objetivo Q2 2025 | Objetivo Anual |
|---------|---------------|------------------|----------------|
| **Lead Time** | 3 semanas | 3 días | 1 día |
| **Deploy Frequency** | 2x mes | Diario | On-demand |
| **MTTR** | 4 horas | 30 minutos | 15 minutos |
| **Change Failure Rate** | 25% | 10% | 5% |

### 📈 Dashboard en Tiempo Real

- [Grafana Dashboard](https://grafana.att.com/d/devsecops-cmit) - Métricas operacionales
- [Datadog APM](https://app.datadoghq.com/apm) - Performance de aplicaciones  
- [SonarQube](https://sonar.att.com/dashboard?id=cmit-devsecops) - Calidad de código

## 🔒 Seguridad

### Controles Implementados

- 🔍 **SAST**: Análisis estático con SonarQube y CodeQL
- 🔍 **DAST**: Testing dinámico con OWASP ZAP
- 🔍 **SCA**: Análisis de dependencias con Snyk
- 🔍 **Secrets**: Detección con TruffleHog y GitHub Secret Scanning
- 🔍 **Containers**: Scanning con Aqua Security
- 🔍 **Infrastructure**: Validación con Checkov

### Reportar Vulnerabilidades

Ver [SECURITY.md](SECURITY.md) para el proceso completo de reporte de vulnerabilidades.

**Contacto rápido**: security@att.com

## 🚀 Deployment

### Entornos

| Entorno | URL | Branch | Auto-Deploy |
|---------|-----|--------|-------------|
| **Development** | https://dev-devsecops.att.com | `develop` | ✅ |
| **Staging** | https://staging-devsecops.att.com | `release/*` | ✅ |
| **Production** | https://devsecops.att.com | `main` | Manual |

### Proceso de Release

```bash
# 1. Crear release branch
git checkout develop
git pull origin develop
git checkout -b release/v2.1.0

# 2. Update version y changelog
npm version patch
npm run changelog

# 3. Create pull request to main
# 4. Después del merge, crear tag
git tag -a v2.1.0 -m "Release v2.1.0"
git push origin v2.1.0

# 5. Deploy automático vía GitHub Actions
```

## 📈 Roadmap

### ✅ Completado (Q1 2025)
- [x] Setup inicial del proyecto
- [x] CI/CD pipeline básico
- [x] Controles de seguridad fundamentales
- [x] Métricas DORA baseline

### 🔄 En Progreso (Q2 2025)
- [ ] ArgoCD integration completa
- [ ] Self-hosted runners setup
- [ ] Advanced security automation
- [ ] Performance optimization

### 📋 Planificado (Q3-Q4 2025)
- [ ] Multi-region deployment
- [ ] Advanced monitoring dashboards
- [ ] ML-powered security insights
- [ ] Complete GitOps implementation

## 🤝 Contributing

### Proceso de Contribución

1. **Fork** el repositorio
2. **Crear** feature branch (`git checkout -b feature/nueva-funcionalidad`)
3. **Desarrollar** siguiendo coding standards
4. **Ejecutar** tests y validaciones
5. **Commit** con mensaje descriptivo (`git commit -m 'feat: nueva funcionalidad'`)
6. **Push** branch (`git push origin feature/nueva-funcionalidad`)
7. **Crear** Pull Request

### Coding Standards

- Seguir [Conventional Commits](https://www.conventionalcommits.org/)
- Usar ESLint y Prettier para formatting
- Escribir tests para nueva funcionalidad
- Documentar APIs con OpenAPI/Swagger
- Mantener coverage >85%

### Code Review Checklist

- [ ] Código cumple con security guidelines
- [ ] Tests incluidos y pasando
- [ ] Documentación actualizada
- [ ] Performance impact evaluado
- [ ] Breaking changes documentados

## 📞 Support y Contacto

### 👥 Team Contacts

- **DevSecOps Lead**: john.doe@att.com
- **Security Champion**: jane.smith@att.com  
- **Infrastructure Lead**: bob.wilson@att.com
- **Team Email**: cmit-devsecops@att.com

### 💬 Communication Channels

- **Slack**: #cmit-devsecops
- **Teams**: AT&T CMIT DevSecOps
- **Jira**: [CMIT Project](https://att.atlassian.net/browse/CMIT)

### 🆘 Emergency Contacts

- **24/7 Hotline**: +1-XXX-XXX-XXXX
- **Incident Response**: ir-team@att.com
- **Security Emergency**: security-emergency@att.com

## 📄 License

Este proyecto está licenciado bajo la licencia MIT - ver el archivo [LICENSE](LICENSE) para detalles.

## 🙏 Acknowledgments

- AT&T CMIT Team por el soporte continuo
- DevSecOps community por las mejores prácticas
- Open source contributors por las herramientas utilizadas

---

**Última actualización**: Enero 2025  
**Mantenido por**: AT&T CMIT DevSecOps Team  
**Versión**: 2.1.0
