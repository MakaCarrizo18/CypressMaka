# CypressMaka
repo/Test/IA

# README para Repositorio de Cypress

Te presento un README profesional y completo para tu repositorio de Cypress:

```markdown
# Cypress Test Automation

Automatización de pruebas end-to-end (E2E) utilizando **Cypress**. Este repositorio contiene suite de pruebas para validar la funcionalidad y el comportamiento de la aplicación web.

## 📋 Contenido

- Pruebas end-to-end automatizadas
- Configuración de Cypress
- Fixtures y datos de prueba
- Comandos personalizados
- Reportes de ejecución

## 🚀 Requisitos previos

- **Node.js** versión 16 o superior
- **npm** o **yarn**
- Un navegador moderno (Chrome, Firefox, Edge, etc.)

## 📦 Instalación

1. Clona el repositorio:
```bash
git clone https://github.com/tu-usuario/cypress-tests.git
cd cypress-tests
```

2. Instala las dependencias:
```bash
npm install
```

3. Verifica que Cypress está instalado correctamente:
```bash
npx cypress --version
```

## ⚙️ Configuración

Edita el archivo `cypress.config.js` para configurar:

- **baseUrl**: URL base de tu aplicación
- **viewportWidth** y **viewportHeight**: Dimensiones de la ventana
- **requestTimeout**: Tiempo de espera para solicitudes HTTP
- **Navegadores** soportados

Ejemplo básico:
```javascript
module.exports = {
  e2e: {
    baseUrl: 'http://localhost:3000',
    viewportWidth: 1280,
    viewportHeight: 720,
    requestTimeout: 10000,
  },
};
```

## 🧪 Estructura del proyecto

```
cypress/
├── e2e/                    # Archivos de pruebas
│   ├── login.cy.js
│   ├── dashboard.cy.js
│   └── ...
├── fixtures/               # Datos de prueba
│   └── users.json
├── support/                # Comandos y configuración
│   ├── commands.js
│   └── e2e.js
└── screenshots/            # Capturas de pantalla (generadas)
```

## 🎯 Ejecutar pruebas

### Modo interactivo (Cypress GUI)
```bash
npm run cypress:open
```

### Modo headless (línea de comandos)
```bash
npm run cypress:run
```

### Ejecutar pruebas específicas
```bash
npx cypress run --spec "cypress/e2e/login.cy.js"
```

### Ejecutar en navegador específico
```bash
npx cypress run --browser chrome
```

## 📊 Reportes

Los reportes se generan automáticamente después de ejecutar las pruebas en modo headless. Consulta la carpeta `cypress/screenshots/` para ver capturas de pantalla de fallos.

## 🛠️ Scripts disponibles

Agrega estos scripts a tu `package.json`:

```json
{
  "scripts": {
    "cypress:open": "cypress open",
    "cypress:run": "cypress run",
    "cypress:run:chrome": "cypress run --browser chrome",
    "cypress:run:firefox": "cypress run --browser firefox",
    "cypress:run:headless": "cypress run --headless"
  }
}
```

## ✍️ Escribir pruebas

Ejemplo básico de una prueba:

```javascript
describe('Login', () => {
  beforeEach(() => {
    cy.visit('/login');
  });

  it('Debe iniciar sesión con credenciales válidas', () => {
    cy.get('input[name="email"]').type('usuario@example.com');
    cy.get('input[name="password"]').type('password123');
    cy.get('button[type="submit"]').click();
    cy.url().should('include', '/dashboard');
    cy.contains('Bienvenido').should('be.visible');
  });

  it('Debe mostrar error con credenciales inválidas', () => {
    cy.get('input[name="email"]').type('usuario@example.com');
    cy.get('input[name="password"]').type('wrongpassword');
    cy.get('button[type="submit"]').click();
    cy.contains('Credenciales inválidas').should('be.visible');
  });
});
```

## 📝 Buenas prácticas

- ✅ Usa **selectores específicos** (atributos data-testid preferentemente)
- ✅ Implementa **Page Object Model** para pruebas complejas
- ✅ Agrupa pruebas relacionadas con `describe()`
- ✅ Usa **fixtures** para datos reutilizables
- ✅ Mantén las pruebas **independientes** entre sí
- ✅ Evita **esperas hard-coded** (cy.wait), usa ciprés wait implícito

## 🐛 Solución de problemas

**Las pruebas no encuentran elementos:**
- Verifica que los selectores sean correctos
- Asegúrate de que los elementos estén visibles
- Usa `cy.debug()` para inspeccionar

**Timeout en solicitudes HTTP:**
- Aumenta `requestTimeout` en `cypress.config.js`
- Verifica el estado del servidor de pruebas

**Problemas de dependencia:**
```bash
rm -rf node_modules package-lock.json
npm install
```

## 📚 Recursos útiles

- [Documentación oficial de Cypress](https://docs.cypress.io)
- [Best Practices](https://docs.cypress.io/guides/references/best-practices)
- [API Reference](https://docs.cypress.io/api/table-of-contents)

## 🤝 Contribuir

1. Crea una rama para tu feature (`git checkout -b feature/nueva-prueba`)
2. Haz commit de tus cambios (`git commit -m 'Agrega nuevas pruebas'`)
3. Push a la rama (`git push origin feature/nueva-prueba`)
4. Abre un Pull Request

## 📄 Licencia

Este proyecto está licenciado bajo la **MIT License** - ver el archivo `LICENSE` para más detalles.

## ✉️ Contacto

Si tienes preguntas o sugerencias, abre un issue en el repositorio.

---

**Última actualización:** Mayo 2026
```

---

## 🎨 Personalización

Puedes **adaptar este README** según tus necesidades:

- **Reemplaza** `tu-usuario` con tu usuario de GitHub
- **Ajusta** los scripts según tus convenciones de nombres
- **Agrega** información sobre tu aplicación específica
- **Incluye** detalles sobre CI/CD si integras con GitHub Actions

¿Necesitas ayuda para configurar **GitHub Actions** o agregar **reportes con Mochawesome**?
