# Getting Started

## BotVox Cli

to install BotVox globally open up any command prompt and type:

```bash
npm install -g botvox
```

Once Installation has finished type ``botvox`` on the commandline, you should see a commandline output like below:

![bv-1](https://github.com/bot-vox/botv-resources/blob/main/_resources/bv-1.png?raw=true)

As you can see in above screenshots botvox provide 3 execution Contexts or flows,

* Vox ``--vox``
* Install ``--install``
* List ``--list``

If you are starting botvox with the ``--vox`` flag, botvox expects you supply an internal Execution Process or flow.

Execution or Process flows are just Javascript classes that live in the ``vox-vault`` i.e.
in:

1. ``botvox\vox-vault``
2. ``botvox\vox-vault\extensions\vox-strategies``
3. ``botvox\vox-vault\extensions\vox-alerts``

As a general thumb of rule

1. everything that lives in ``botvox\vox-vault`` is considered a Simple Vox and will be phased out in future releases

2. everything that lives in ``botvox\vox-vault\extensions\vox-strategies`` is considered a VoxEngine Strategy execution flow, meaning the ``--vox`` argument is supplied like this ``--vox=VoxEngine`` and needs to be followed by the ``--strategy`` flag to make sure the VoxEngine can pick up the target Strategy to execute!

3. everything that lives in ``botvox\vox-vault\extensions\vox-alerts`` is considered a VoxEngine Alert execution flow, meaning the ``--vox`` argument is supplied like this ``--vox=VoxEngine`` and needs to be followed by the ``--alert`` flag to make sure the VoxEngine can pick up the target Alerting implementation to execute!

To get a better sense on what is possible with botvox, we recommend to start exploring the cli by typing ```botvox --help```

![bv-2](https://github.com/bot-vox/botv-resources/blob/main/_resources/bv-2.png?raw=true)
