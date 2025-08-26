# Copilot Instructions for homebridge-unifi-network

## Project Overview
This is a TypeScript-based Homebridge plugin that provides HomeKit integration for UniFi SmartPower devices including PDU Pro, Smart Plugs, Smart Strips, and Gateway Pro devices. The plugin connects to UniFi controllers to monitor and control power outlets and PoE switch ports.

## Code Style & Standards

### TypeScript Guidelines
- Use strict TypeScript compilation settings
- Prefer interfaces over types for object definitions
- Use proper type annotations for all function parameters and return values
- Follow existing patterns for async/await usage
- Use proper error handling with try/catch blocks

### Code Formatting
- Use ESLint configuration in `.eslintrc.yaml` with max 0 warnings
- Use Prettier configuration in `.prettierrc.yaml` for consistent formatting
- Run `npm run lint` before committing changes
- Use `npm run lint-fix` to automatically fix formatting issues

### File Structure
- Main source code in `src/` directory
- Compiled output in `dist/` directory (git-ignored)
- Configuration schema in `config.schema.json`
- Follow existing module organization patterns

## Development Workflow

### Building and Testing
- Always run `npm run build` to compile TypeScript
- Use `npm run lint` to check code quality
- Test script is currently `npm run eslint` - run this before commits
- Use `npm run watch` for development with auto-restart

### Dependencies
- Prefer existing dependencies over adding new ones
- Key dependencies include:
  - `node-unifi` for UniFi API communication
  - `cache-manager` and `cacheable` for caching
  - `async-lock` for synchronization
  - `pubsub-js` for event handling

## Homebridge Plugin Patterns

### Platform Plugin Structure
- Main platform class should extend `StaticPlatformPlugin` or `DynamicPlatformPlugin`
- Use proper Homebridge logging with `this.log`
- Follow Homebridge accessory lifecycle patterns
- Implement proper cleanup in `configureAccessory` and platform shutdown

### Configuration Handling
- Validate configuration against `config.schema.json`
- Provide sensible defaults for optional configuration
- Support include/exclude patterns for sites, devices, outlets, and ports
- Handle authentication properly with support for local users

### Device Management
- Use proper caching for device status (default 15s TTL)
- Implement polling intervals for device discovery (default 600s) and status updates (default 15s)
- Handle device state changes gracefully
- Support control switches for safety

### HomeKit Services
- Use appropriate HomeKit service types for outlets and switches
- Implement proper characteristic handling for On/Off state
- Handle errors gracefully and provide meaningful logging
- Follow HomeKit naming conventions

## API Integration

### UniFi Controller Communication
- Use `node-unifi` library for API calls
- Implement proper authentication handling
- Support both local and cloud key controllers
- Handle API rate limiting and caching appropriately

### Error Handling
- Provide clear error messages for common issues (authentication, connectivity)
- Log appropriate debug information without exposing sensitive data
- Handle network timeouts and retries gracefully

## Security Considerations
- Never log passwords or sensitive authentication data
- Support 2FA authentication flows
- Recommend local user accounts over admin credentials
- Validate all user inputs from configuration

## Documentation
- Update README.md for any new configuration options
- Follow existing documentation patterns for configuration examples
- Include clear examples in JSON format
- Document any breaking changes in commit messages

## Common Patterns
- Use existing caching patterns with `cache-manager`
- Follow async/await patterns consistently
- Use proper TypeScript types for UniFi API responses
- Implement proper event handling with `pubsub-js`
- Use `async-lock` for preventing concurrent API calls

## Testing Guidelines
- Ensure ESLint passes with zero warnings
- Test with actual UniFi hardware when possible
- Verify configuration schema changes work correctly
- Test include/exclude filtering functionality

## Commit Guidelines
- Use conventional commit format when possible
- Include issue numbers in commit messages
- Make atomic commits with clear purposes
- Run lint before committing