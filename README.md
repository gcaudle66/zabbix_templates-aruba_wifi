
# HP Enterprise Wireless Switch by SNMP - Zabbix Template

## Overview

This Zabbix template provides monitoring for **HP/Aruba Wireless Controllers** and **Access Points (APs)** via SNMP. It is designed for Zabbix 7.x and utilizes Low-Level Discovery (LLD) to automatically detect and monitor HP/Aruba wireless devices.

The template includes several OIDs and macros to retrieve important metrics for each AP, including status, model, IP address, uptime, firmware version, and more.

## Features

This template enables monitoring of the following parameters for HP/Aruba wireless controllers and APs:

- **AP Status**: Indicates the current operational status of each AP.
- **AP Name**: The configured name of each AP.
- **MAC Address**: MAC address of the AP.
- **IP Address**: IP address assigned to the AP.
- **Model**: Model identifier of the AP.
- **Uptime**: Total uptime of the AP since its last reboot.
- **Group**: AP group or cluster to which the AP belongs.
- **Software Version**: Firmware version running on the AP.
- **Serial Number**: Serial number of the AP.
- **Primary Controller**: Primary controller information for the AP.
- **Secondary Controller**: Secondary controller information for the AP (if applicable).

## Template Details

| **Type** | **OID**                               | **Description**  | **LLD Macro**  |
|----------|---------------------------------------|------------------|----------------|
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.19` | AP Status       | `{#AP.STATUS}` |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.3`  | AP Name         | `{#AP.NAME}`   |
| INDEX    | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.1`  | MAC Address     | `{#AP.MAC}`    |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.2`  | IP Address      | `{#AP.IP}`     |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.13` | Model           | `{#AP.MODEL}`  |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.12` | Uptime          | `{#AP.UPTIME}` |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.4`  | Group           | `{#AP.GROUP}`  |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.34` | Software Version| `{#AP.SW}`     |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.6`  | Serial Number   | `{#AP.SN}`     |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.39` | Primary Controller | `{#AP.SW1}`  |
| OID      | `.1.3.6.1.4.1.14823.2.2.1.5.2.1.4.1.40` | Secondary Controller | `{#AP.SW2}`  |

## Installation

1. Download the template file: [zbx_aruba_hp_wireless-template.yaml](zbx_aruba_hp_wireless-template.yaml).
2. Import the template into Zabbix:
   - Go to **Configuration** > **Templates**.
   - Click **Import** and select the YAML file.
3. Link the template to the appropriate host (HP/Aruba wireless controller or AP).
4. Ensure SNMP is enabled on the monitored device and that Zabbix has the correct SNMP credentials configured.

## Requirements

- **Zabbix 7.x**
- **SNMP enabled** on HP/Aruba wireless controllers and APs
- **Network Connectivity** between Zabbix server and the wireless devices

## Usage

Once the template is linked to the host, Zabbix will begin discovering and monitoring all APs managed by the controller. Each discovered AP will appear in Zabbix under the host, providing real-time metrics based on the above parameters.

### Example Screenshots

*(Add example screenshots here if available to demonstrate template usage in Zabbix)*

## Troubleshooting

1. **No Data Appearing for APs**:
   - Verify SNMP connectivity between Zabbix and the device.
   - Ensure SNMP community strings or SNMP v3 credentials are correctly configured.
2. **Incorrect or Missing Metrics**:
   - Check the firmware version of your HP/Aruba devices, as older versions may not support certain OIDs.
   - Verify that the APs are properly configured and managed by the controller.

## Additional Information

This template leverages the following MIB OIDs for data collection:
- **Aruba Enterprise MIBs**: OIDs in the `.1.3.6.1.4.1.14823` namespace

For more details on Aruba/HP Enterprise MIBs, refer to [Aruba Networks Documentation](https://www.arubanetworks.com/).

## License

This Zabbix template is open-source and can be modified to fit your needs. However, please attribute the original author if redistributed.
