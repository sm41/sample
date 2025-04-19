You can install yt-dlp either using one of the official releases, or with your favorite package manager

> If you are unfamiliar with the command line, you may use one of the many third-party GUIs available

---

# Installing the release binary

You can simply download the [correct binary file](https://github.com/yt-dlp/yt-dlp#release-files) for your OS

[![Windows](https://img.shields.io/badge/-Windows_x64-blue.svg?style=for-the-badge&logo=windows)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe)
[![Linux](https://img.shields.io/badge/-Linux/BSD-red.svg?style=for-the-badge&logo=linux)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp)
[![MacOS](https://img.shields.io/badge/-MacOS-lightblue.svg?style=for-the-badge&logo=apple)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos)
[![Other variants](https://img.shields.io/badge/-Other-grey.svg?style=for-the-badge)](https://github.com/yt-dlp/yt-dlp#release-files)

In UNIX-like OSes (MacOS, Linux, BSD), you can also install the application into a location in your `$PATH`, such as `~/.local/bin`, in one of the following ways:

```bash
curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o ~/.local/bin/yt-dlp
chmod a+rx ~/.local/bin/yt-dlp  # Make executable
```

```bash
wget https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -O ~/.local/bin/yt-dlp
chmod a+rx ~/.local/bin/yt-dlp  # Make executable
```

```bash
aria2c https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp --dir ~/.local/bin -o yt-dlp
chmod a+rx ~/.local/bin/yt-dlp  # Make executable
```

To update, run:
```bash
yt-dlp -U
```

To use shell completion (autocomplete), look for the completion files in the [source tarball](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.tar.gz). It comes with bash, fish & zsh support.

# With [pip](https://pypi.org/project/pip)

You can install the [PyPI package](https://pypi.org/project/yt-dlp) with:
```bash
python3 -m pip install -U "yt-dlp[default]"
```

You can install without any of the optional dependencies using:
```bash
python3 -m pip install --no-deps -U yt-dlp
```
<a id="pip-nightly"></a>

You can also install the nightly version of yt-dlp with:
```bash
python3 -m pip install -U --pre "yt-dlp[default]"
```

<a id="pip-master"></a>

If you want to be on the bleeding edge, you can also install the master branch with:
```bash
python3 -m pip install -U pip hatchling wheel
python3 -m pip install --force-reinstall "yt-dlp[default] @ https://github.com/yt-dlp/yt-dlp/archive/master.tar.gz"
```

On some systems, you may need to use `py` or `python` instead of `python3`

To update, run:
```bash
python3 -m pip install -U "yt-dlp[default]"