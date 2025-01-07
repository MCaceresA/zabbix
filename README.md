![Ejemplo de imagen externa](https://assets.zabbix.com/dist/images/logo.fd87efa6da9bed3fd8c9.svg)


# Nginx File Discovery Template for Zabbix

## Description

This Zabbix template is designed to monitor and discover Nginx configuration files and site files automatically. It provides insights into changes and counts of files in specified directories, ensuring that your Nginx configurations are always under control.

### Features

1. **File Count Monitoring**:
   - Monitors the number of files in `/etc/nginx/sites-enabled`.
   - Triggers an alert when the number of files changes.

2. **Configuration File Discovery**:
   - Discovers files in the `/etc/nginx/conf.d/` directory.
   - Triggers an alert when a file in this directory is modified.

3. **Site File Discovery**:
   - Discovers files in the `/etc/nginx/sites-enabled/` directory.
   - Triggers an alert when a site file is modified.

### Requirements

- Zabbix version: 6.0 or higher
- Nginx installed on the monitored host

### Macros Used

| Macro                | Default Value               | Description                  |
|----------------------|-----------------------------|------------------------------|
| `{$FOLDER.CONFD}`    | `/etc/nginx/conf.d/`        | Path to the `conf.d` folder. |
| `{$FOLDER.SITES.ENABLED}` | `/etc/nginx/sites-enabled/` | Path to the `sites-enabled` folder. |

### Items and Triggers

- **Items**:
  - `Nginx sites count`: Counts files in `/etc/nginx/sites-enabled`.
  - `Nginx conf.d : {#NGINX.CONFD.BASENAME}`: Discovers and monitors files in the `conf.d` directory.
  - `Nginx Site : {#NGINX.BASENAME}`: Discovers and monitors files in the `sites-enabled` directory.

- **Triggers**:
  - Alert if a new file is added or removed in `/etc/nginx/sites-enabled`.
  - Alert if any file in `conf.d` or `sites-enabled` is modified.

## Installation

1. Download the template file: `Nginx_FileDiscovery.yaml`.
2. Import the template into Zabbix:
   - Go to `Configuration` > `Templates` > `Import`.
   - Choose the `Nginx_FileDiscovery.yaml` file and import it.
3. Link the template to the desired host(s).

## Usage

Once the template is linked, Zabbix will automatically start monitoring and discovering files based on the specified paths. Alerts will be triggered if there are any changes to the monitored files or directories.

## Notes

- Ensure that the Zabbix agent running on the host has the necessary permissions to access the specified directories.
- Modify the macros (`{$FOLDER.CONFD}` and `{$FOLDER.SITES.ENABLED}`) if your Nginx configuration directories differ from the defaults.

## Contributing

Feel free to open issues or submit pull requests to improve this template. Contributions are always welcome!

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
