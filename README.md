# Meta-Coura

![Meta-Coura running across Saturn's rings](assets/meta-coura.gif)

Meta-Coura adds signed delegation to the [Coura](https://github.com/petronushowcore-mx/notification-courier)
family. The receiver verifies the delegate and request against a local
registration, then records the decision and any local effect in SQLite.

The same valid signed request can arrive in two delivery attempts. Meta-Coura
commits the effect once and keeps the ID of the attempt that first committed it.
Records without an originating attempt return `UNMEASURED`. Coura's transport
receipt still describes the current delivery.

## Try it locally

Install Python 3.10+ and Git, then run:

```sh
git clone https://github.com/petronushowcore-mx/meta-coura.git
cd meta-coura
python -m venv .venv
```

Activate `.venv`, then run:

```sh
python -m pip install -r requirements.txt
python meta_coura.py demo --workdir ./meta-demo
python tests/check_meta_coura.py
```

The demo routes synthetic signed requests through Coura to a local receiver.
The receiver supports a stored note and a bounded SQLite fixture append. See
the [protocol and command reference](docs/meta-coura.md) for the signature
format, registration, receipts and trust boundaries. The [examples](examples/)
show the receiver registration fields and Coura command configuration.

MIT · MxBv · The Urgrund R&D Lab
