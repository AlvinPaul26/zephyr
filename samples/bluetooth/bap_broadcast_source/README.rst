.. zephyr:code-sample:: bluetooth_bap_broadcast_source
   :name: Basic Audio Profile (BAP) Broadcast Audio Source
   :relevant-api: bluetooth bt_audio bt_bap

   Use BAP Broadcast Source functionality.

Overview
********

Application demonstrating the BAP Broadcast Source functionality.
Will start advertising extended advertising with audio flags, periodic advertising with the
Broadcast Audio Source Endpoint (BASE) and finally the BIGinfo together with
(mock) Audio (ISO) data.

The BAP Broadcast Source will reset every 30 seconds to show the full API.

This sample can be found under
:zephyr_file:`samples/bluetooth/bap_broadcast_source` in the Zephyr tree.

Check the :zephyr:code-sample-category:`bluetooth` samples for general information.

Requirements
************

* BlueZ running on the host, or
* A board with Bluetooth Low Energy 5.2 support

Building and Running
********************

When building targeting an nrf52 series board with the Zephyr Bluetooth Controller,
use ``-DEXTRA_CONF_FILE=overlay-bt_ll_sw_split.conf`` to enable the required ISO
feature support.
The sample defaults to sequential packing of BIS subevents, add
``-DCONFIG_ISO_PACKING_INTERLEAVED=y`` to use interleaved packing.

Building for an nrf5340dk
-------------------------

You can build both the application core image and an appropriate controller image for the network
core with:

.. zephyr-app-commands::
   :zephyr-app: samples/bluetooth/bap_broadcast_source/
   :board: nrf5340dk/nrf5340/cpuapp
   :goals: build
   :west-args: --sysbuild

If you prefer to only build the application core image, you can do so by doing instead:

.. zephyr-app-commands::
   :zephyr-app: samples/bluetooth/bap_broadcast_source/
   :board: nrf5340dk/nrf5340/cpuapp
   :goals: build

In that case you can pair this application core image with the
:zephyr:code-sample:`bluetooth_hci_ipc` sample
:zephyr_file:`samples/bluetooth/hci_ipc/nrf5340_cpunet_iso-bt_ll_sw_split.conf` configuration.

Building for a simulated nrf5340bsim
------------------------------------

Similarly to how you would for real HW, you can do:

.. zephyr-app-commands::
   :zephyr-app: samples/bluetooth/bap_broadcast_source/
   :board: nrf5340bsim/nrf5340/cpuapp
   :goals: build
   :west-args: --sysbuild

Note this will produce a Linux executable in :file:`./build/zephyr/zephyr.exe`.
For more information, check :ref:`this board documentation <nrf5340bsim>`.

Building for a simulated nrf52_bsim
-----------------------------------

.. zephyr-app-commands::
   :zephyr-app: samples/bluetooth/bap_broadcast_source/
   :board: nrf52_bsim
   :goals: build
   :gen-args: -DEXTRA_CONF_FILE=overlay-bt_ll_sw_split.conf
