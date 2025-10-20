# Cheesy Store for Runtipi

A custom app store for the Runtipi platform featuring additional applications not found in the main repository.

## Supported Applications

- **[Duplicacy](https://duplicacy.com)**: Enterprise backup solution with client-side encryption and deduplication
- **[Nginx Proxy Manager](https://nginxproxymanager.com)**: Easy-to-use nginx proxy management with SSL support
- **[SearXNG](https://docs.searxng.org)**: Privacy-respecting metasearch engine
- **[Stash](https://stashapp.cc)**: A self-hosted organizer for your media collections
- **[Twingate](https://www.twingate.com)**: Modern Zero Trust remote access solution

## Installation

1. Open your Runtipi dashboard
2. Navigate to Settings > App Stores
3. Click "Add Custom App Store"
4. Enter the following information:
   - Name: Cheesy Store
   - URL: `https://raw.githubusercontent.com/YOUR_USERNAME/runtipi-cheesystore/main`
   - Branch: main
5. Click "Add Store"

The custom apps will now appear in your Runtipi app catalog, ready to install.

## Repository Structure

- **apps/**: Contains individual app directories
  - Each app has its own folder with the following structure:
    - `config.json`: App configuration file
    - `docker-compose.json`: Docker setup for the app
    - `metadata/`: Contains app visuals and descriptions
      - `description.md`: Markdown description of the app
      - `logo.jpg`: App logo image

- **tests/**: Contains test files for the app store
  - `apps.test.ts`: Test suite for validating apps

## Documentation

For detailed instructions on creating your own app store, please refer to the official guide:
[Create Your Own App Store Guide](https://runtipi.io/docs/guides/create-your-own-app-store)

## Contributing

Feel free to contribute by submitting pull requests with new applications or improvements to existing ones.