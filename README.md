# SimpleMCPClient

A Rust-based Master Control Program (MCP) server that provides LDAP user information querying capabilities.

## Overview

SimpleMCPClient is a lightweight server application written in Rust that acts as an intermediary between clients and LDAP directories. It provides a simple interface to query and retrieve user information from LDAP databases while maintaining security and performance.

## Features

- LDAP user information querying using Rust's LDAP client libraries
- Secure connection handling with TLS support
- Configurable LDAP server settings
- User authentication support
- Efficient data caching
- RESTful API interface using Actix-web
- Async/await support for high performance
- Strong type safety and error handling

## Prerequisites

- Rust (latest stable version)
- Cargo (Rust's package manager)
- OpenLDAP or compatible LDAP server
- Network access to the LDAP server

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/SimpleMCPClient.git
cd SimpleMCPClient
```

2. Install Rust if you haven't already:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

3. Build the project:
```bash
cargo build --release
```

## Project Structure

```
SimpleMCPClient/
├── src/
│   ├── main.rs           # Application entry point
│   ├── config.rs         # Configuration management
│   ├── ldap/             # LDAP client implementation
│   ├── api/              # REST API handlers
│   ├── models/           # Data structures
│   └── utils/            # Utility functions
├── tests/                # Integration and unit tests
├── Cargo.toml            # Project dependencies
└── .env                  # Environment configuration
```

## Configuration

Create a `.env` file in the project root with the following variables:

```env
LDAP_SERVER=ldap://your-ldap-server:389
LDAP_BASE_DN=dc=example,dc=com
LDAP_BIND_DN=cn=admin,dc=example,dc=com
LDAP_BIND_PASSWORD=your_password
MCP_SERVER_PORT=8080
```

## Usage

1. Start the server:
```bash
cargo run --release
```

2. The server will be available at `http://localhost:8080`

### API Endpoints

- `GET /users` - List all users
- `GET /users/{username}` - Get specific user details
- `POST /users/search` - Search users with custom filters

## Development

### Dependencies

The project uses several key Rust crates:
- `actix-web` for the web server
- `ldap3` for LDAP operations
- `dotenv` for environment configuration
- `serde` for serialization/deserialization
- `tokio` for async runtime
- `log` and `env_logger` for logging

### Building

```bash
# Debug build
cargo build

# Release build
cargo build --release
```

### Testing

```bash
# Run all tests
cargo test

# Run specific test
cargo test test_name

# Run tests with logging
RUST_LOG=debug cargo test
```

### Running in Development Mode

```bash
# Development mode with logging
RUST_LOG=debug cargo run

# Release mode
cargo run --release
```

### Code Formatting

```bash
cargo fmt
```

### Linting

```bash
cargo clippy
```

## Security Considerations

- All LDAP connections are encrypted using TLS
- Credentials are stored securely using environment variables
- Rate limiting is implemented using actix-web middleware
- Input validation is performed on all queries
- Memory safety guaranteed by Rust's ownership model

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Rust community for the excellent ecosystem
- OpenLDAP project for the LDAP implementation
- Actix-web team for the web framework
- All contributors to the Rust LDAP ecosystem 