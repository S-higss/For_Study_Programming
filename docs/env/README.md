# �J����

## �ڎ�
- [��](#��)
- [�J�����\�z](#�J�����\�z)
    - [Python�̃C���X�g�[��](#python�̃C���X�g�[��)
    - [pip�̃C���X�g�[��](#pip�̃C���X�g�[��)
    - [make�̃C���X�g�[��](#make�̃C���X�g�[��)

## ��

OS: Windows10/11, Linux

Python: v3.9.6
(�������CLinux�ł�Python: v3.9.x, v3.10.x, v3.11.x �œ���m�F��)

pip: v22.3.1

[TOP �ɖ߂�](#�ڎ�)

[HOME �ɖ߂�](../README.md)

## �J�����\�z

### Python�̃C���X�g�[��
�ȉ���Python3.9�̗�ł����C
���o�[�W�����̏ꍇ��Python3.x��x��C�ӂ̐����ɒu�������Ă��������D

#### Linux���̏ꍇ
apt�𗘗p���ăC���X�g�[������ꍇ��������܂��D

##### apt��update

```bash
sudo apt update
sudo apt install software-properties-common
```

##### Repository��o�^

```bash
sudo add-apt-repository ppa:deadsnakes/ppa
```

##### Python3.9���C���X�g�[��

```bash
sudo apt install python3.9
```

##### Python3.9���C���X�g�[���ł������m�F

```bash
python3.9 --version
```

�����C���X�g�[���ł��Ă���Έȉ��̂悤�ȏo�͂��Ȃ���܂��D(���v3.9.16)

```bash
Python 3.9.16
```

#### Windows���̏ꍇ
�����T�C�g����C���X�g�[�����܂��D
[������](http://netsu-n.mep.titech.ac.jp/~Kawaguchi/python/install-win/)���Q�l�ɂ��Ă��������D
(�Q�l�F�����H�Ƒ�w �H�w�@�@�B�n ����B�珕���y�[�W)

[TOP �ɖ߂�](#�ڎ�)

[HOME �ɖ߂�](../README.md)

### pip�̃C���X�g�[��
pip�̃C���X�g�[���ɂ��ẮCPython3�n���C���X�g�[������Ă��邱�Ƃ�O��ɐ������܂��D

##### pip���C���X�g�[������Ă��邩�̊m�F

```bash
pip -V
��������
pip3 -V
```

pip�̃o�[�W������񂪏o��΃C���X�g�[������Ă��邽�߁C__�ȍ~�̑���͕s�v__ �ł��D
`ModuleNotFoundError: No Module named 'pip'`�Əo�͂��ꂽ���C�G���[���o�͂��ꂽ�ꍇ�C���̃R�}���h�����s���Ă��������D

```bash
python -m pip -V
��������
python3 -m pip -V
```

���̃R�}���h�����s�ł����ꍇ�́C__pip�̓C���X�g�[������Ă��邪�p�X���ʂ��Ă��Ȃ�__ ���ƂɂȂ�܂��D���̏ꍇ��[������]()���Q�Ƃ��Ă��������D
���̃R�}���h�ł��G���[���o�͂��ꂽ�ꍇ�C���ɐi��ŉ������D

##### get-pip.py���_�E�����[�h
- Linux��

```bash
wget https://bootstrap.pypa.io/get-pip.py
```

- Windows��
    1. �_�E�����[�h��Fhttps://bootstrap.pypa.io/get-pip.py ���get-pip.py��C�ӂ̃f�B���N�g���ɕۑ�
    1. �ۑ������f�B���N�g���Ŏ����̃R�}���h�����s

##### python�R�}���h��p����pip���C���X�g�[��

```bash
python get-pip.py
```

##### pip���C���X�g�[�����ꂽ���̊m�F
���@�́C[pip���C���X�g�[������Ă��邩�̊m�F](#pip���C���X�g�[�����ꂽ���̊m�F)�Ɠ��l�ł��D

#### pip�Ƀp�X��ʂ����@
Windows���ł́C��{�I��Python��path���ʂ��Ă����pip�����삷��͂��ł��邽�߁C�ȉ���Linux���ɂ��Đ������Ă��܂��D
���̃R�}���h�ŁCpip��`~/.local/bin`�z���ɒu����Ă��邩�m�F���܂��D

```bash
ls ~/.local/bin
```

���̎��s���ʓ���`pip`��`pip3`���̕\��������΁C�ȉ��̃R�}���h�Ńp�X��ʂ��܂��D
�Ȃ������ꍇ�C`which pip`��pip���u����Ă���p�X���m�F���C`~/.local/bin`�z����pip���ړ����Ă��������D

```bash
export PATH=$PATH:~/.local/bin
```

�p�X��ʂ�����Cpip�R�}���h�����s�ł��邩�m�F���܂��D
���@�́C[pip���C���X�g�[������Ă��邩�̊m�F](#pip���C���X�g�[�����ꂽ���̊m�F)�Ɠ��l�ł��D

[TOP �ɖ߂�](#�ڎ�)

[HOME �ɖ߂�](../README.md)

### make�̃C���X�g�[��
make�͎�Ƃ��āCC�����C++�ȂǃR���p�C���^�̃v���O���~���O����ŋL�q���ꂽ�v���O������e�ՂɃr���h���邽�߂̃c�[���ł��D
�{�V�X�e���ł��C�R�}���h���C���ł̎��s�̊ȗ����̂���Makefile��z�u���g�p���Ă��܂��D

#### Linux���̏ꍇ
apt�𗘗p���ăC���X�g�[������ꍇ��������܂��D

##### apt��update

```bash
sudo apt update
```

##### make���C���X�g�[��

```bash
sudo apt install -y make
```

##### make���C���X�g�[�����ꂽ���̊m�F
���̃R�}���h�����s���Cmake�̃o�[�W������񂪏o��΃C���X�g�[�������ł��D

```bash
make -version
```

#### Windows���̏ꍇ
�����T�C�g����C���X�g�[�����܂��D
[������](https://www.kkaneko.jp/tools/win/make.html)���Q�l�ɂ��Ă��������D
(�Q�l�F���R��w �H�w�����H�w�� ���q�M�F�����y�[�W)

[TOP �ɖ߂�](#�ڎ�)

[HOME �ɖ߂�](../README.md)