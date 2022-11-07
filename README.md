# Netbox Device Type Import Min

This library is intended to be your friend and help you import all the device-types defined within the the [NetBox Device Type Library Repository](https://github.com/netbox-community/devicetype-library).

## 🚀 Getting Started

1. This script is written in Python, so lets setup a virtual environment.

```bash
git clone https://github.com/M3i-dev/devicetype-library-import-min.git
cd devicetype-library-import-min
python3 -m venv venv
source venv/bin/activate
```

2. Now that we have the basics setup, we'll need to install the requirements.

```bash
pip install -r requirements.txt
```

3. There are two variables that are required when using this script to import device types into your Netbox installation. (1) Your Netbox instance URL and (2) a token with **write rights**.

Copy the existing `.env.example` to your own `.env` file, and fill in the variables.

```
cp .env.example .env
nano .env
```

Finally, we are able to execute the script and import some device templates!

## 🔌 Usage

To use the script, simply execute the script as follows. Make sure you're still in the activated virtual environment we created before.

```
./nb-dt-import.py
```

This will clone the latest master branch from the `m3i-dev/devicetype-library-min` from Github and install it into the `repo` subdirectory. If this directory already exists, it will perform a `git pull` to update the reposity instead.

Next, it will loop over every manufacturer and every device of every manufacturer and begin checking if your Netbox install already has them, and if not, creates them. It will skip preexisting manufacturers, devices, interfaces, etc. so as to not end up with duplicate entries in your Netbox instance.
