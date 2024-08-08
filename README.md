# qa-automation-assignment

## What will be evaluated
- Completion of requirements
- Code quality & design
- Readability of tests, how easy it is to understand scope of test case
- How easy it is to run tests and to interpret results

## Description
The UniFi Network Application is part of the UniFi ecosystem by Ubiquiti. It serves as a centralized management interface for UniFi Network devices, including gateways, switches, access points, and other network components. 
The application is designed to offer real-time monitoring, configuration, and management of network devices, making it a powerful tool for both home and enterprise networks.

The UniFi Network Application is used for various network management tasks:
- Network Configuration: Set up and configure network settings, SSIDs, VLANs, and more.
- Monitoring and Analytics: Track network performance, bandwidth usage, and device status.
- Security Management: Configure Firewall, VPNs and Threat Management.
- Alerts and Notifications: Set up alerts for network events, such as device disconnections or security breaches.
- and much more..

Self-hosting UniFi Network application allows users to install and manage the UniFi Network Application on various operating systems and hardware setups. This method provides flexibility and customization options.

## Task

As base for any testing with Network application, we must first complete the setup which involves few basic steps - specifying name/country and admin credentials (can use local admin to simplify flow).
See "Additional Notes" below on tips how to get started and execute flow manually.

**Part 1** - Setup Network application via Web UI.
After setup completion we would like to verify that:
- `Dashboard` page -> `Admin Activity` widget lists admin activity with admin name specified in setup step
- `Settings` page -> `System` tab -> `General` section -> `Country/Region` dropdown value matches configuration during setup

**Part 2** - Setup Network application via API.
Use Part 1 as template to observe executed API calls:
- `POST /api/cmd/sitemgr`  '{cmd: "add-default-admin", name: "admin", email: "network-admin@gmail.com", x_password: "password"}' - to create local admin
- `POST /api/set/setting/super_identity` '{name: "UniFi Network"}' - to set application name
- `POST /api/set/setting/country` '{code: "840"}' - to set country/region
- `POST /api/set/setting/locale` '{timezone: "Europe/Riga"}' - to set locale/timezone
- `POST /api/cmd/system` '{cmd: "set-installed"}' - to set configured state
After setup completetion we would like to verify that:
- `GET /api/self` returns admin with configured "name"
- `GET /api/s/default/get/setting/country` returns configured country "code"


Additional notes:
- There's big community of Network Application users and vast set of tools to run and customize it
- [Community maintained docker image](https://hub.docker.com/r/linuxserver/unifi-network-application)
- [Official Network Server download links](https://ui.com/download/releases/network-server)
- After you install the application, Web UI is available via http://127.0.0.1:8080/ or https://127.0.0.1:8443/
- Local admin credentials are available after choosing "Advanced Setup" flow

Recommended tools:
- Docker
- Selenium/Java
- Gradle/Maven

## Submission
- Provide URL to a public repository or send project files as ZIP archive
