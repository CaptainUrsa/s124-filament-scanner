# AGENTS.md - S124 Filament Scanner Frontend

## Repository scope

- This repository contains only the public scanner frontend for the S124 Filament Management System.
- The private backend is maintained separately in `S124-print-flow/filament/Code.gs`.
- Do not duplicate backend Google Apps Script code into this repository.
- The frontend communicates with the backend through the configured Apps Script web-app endpoint.
- Preserve compatibility with the existing backend API unless a coordinated frontend/backend change is explicitly requested.

## Architecture

Public scanner frontend → HTTPS → Apps Script filament backend → Google Sheets

The browser provides the scanner interface and submits requests. The Apps Script backend owns authentication, barcode registration, catalogue and inventory validation, and authoritative writes to Google Sheets.

## Security and data authority

- Never place PINs, credentials, spreadsheet IDs, Script IDs, or other private configuration into this public repository.
- Treat barcode registration, inventory changes, and operator authentication as security-sensitive workflows.
- Do not weaken authentication or move authoritative inventory validation into the browser.
- Inventory and catalogue data in the browser are not authoritative. The backend remains authoritative.
- When changing API requests or response handling, identify whether a corresponding backend change is required.

## Frontend constraints

- Keep the scanner suitable for mobile browsers and physical barcode-scanning workflows.
- Avoid unnecessary frameworks or dependencies.
- Preserve the lightweight static frontend architecture unless explicitly requested otherwise.

## Deployment and publishing

- Do not deploy or push changes automatically unless explicitly requested.
