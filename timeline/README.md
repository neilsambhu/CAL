10/19/2023 1:17:50 PM: for creating the conda environment, pytorch fails:
```
(base) nsambhu@CSE001022:~/github/CAL$ conda env create -f environment.yml 
Collecting package metadata (repodata.json): done
Solving environment: failed

ResolvePackageNotFound: 
  - pytorch==1.1.0=py3.6_cuda10.0.130_cudnn7.5.1_0
```
10/19/2023 1:21:51 PM: potential solution to pytorch install: https://stackoverflow.com/a/76110134 
```
pip install --index-url https://download.pytorch.org/whl/ torch==1.0.0
```
This solution would be implemented after creating the conda environment CAL.  
10/19/2023 1:22:57 PM: new error from creating conda environment:
```
    Compiling bcolz/carray_ext.pyx because it changed.
    [1/1] Cythonizing bcolz/carray_ext.pyx
    /tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/.eggs/Cython-3.0.4-py3.6-linux-x86_64.egg/Cython/Compiler/Main.py:381: FutureWarning: Cython directive 'language_level' not set, using '3str' for now (Py3). This has changed from earlier releases! File: /tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/bcolz/carray_ext.pxd
      tree = Parsing.p_module(s, pxd, full_module_name)
    
    Error compiling Cython file:
    ------------------------------------------------------------
    ...
            # Create the final container and fill it
            out = carray([], dtype=newdtype, cparams=self.cparams,
                           expectedlen=newlen,
                           rootdir=rootdir, mode='w')
            if newlen < ilen:
                rsize = isize / newlen
                              ^
    ------------------------------------------------------------
    
    bcolz/carray_ext.pyx:1685:26: Cannot assign type 'double' to 'npy_intp'
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/setup.py", line 234, in <module>
        cmdclass=LazyCommandClass(),
      File "/home/nsambhu/.local/lib/python3.6/site-packages/setuptools/__init__.py", line 161, in setup
        return distutils.core.setup(**attrs)
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/core.py", line 148, in setup
        dist.run_commands()
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/dist.py", line 955, in run_commands
        self.run_command(cmd)
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/dist.py", line 974, in run_command
        cmd_obj.run()
      File "/home/nsambhu/.local/lib/python3.6/site-packages/setuptools/command/install.py", line 61, in run
        return orig.install.run(self)
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/command/install.py", line 545, in run
        self.run_command('build')
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/cmd.py", line 313, in run_command
        self.distribution.run_command(command)
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/dist.py", line 974, in run_command
        cmd_obj.run()
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/command/build.py", line 135, in run
        self.run_command(cmd_name)
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/cmd.py", line 313, in run_command
        self.distribution.run_command(command)
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/dist.py", line 974, in run_command
        cmd_obj.run()
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/command/build_ext.py", line 339, in run
        self.build_extensions()
      File "/tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/setup.py", line 77, in build_extensions
        cython_build_ext.build_extensions(self)
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/command/build_ext.py", line 448, in build_extensions
        self._build_extensions_serial()
      File "/home/nsambhu/anaconda3/envs/CAL/lib/python3.6/distutils/command/build_ext.py", line 473, in _build_extensions_serial
        self.build_extension(ext)
      File "/tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/.eggs/Cython-3.0.4-py3.6-linux-x86_64.egg/Cython/Distutils/build_ext.py", line 131, in build_extension
        ext,force=self.force, quiet=self.verbose == 0, **options
      File "/tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/.eggs/Cython-3.0.4-py3.6-linux-x86_64.egg/Cython/Build/Dependencies.py", line 1154, in cythonize
        cythonize_one(*args)
      File "/tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/.eggs/Cython-3.0.4-py3.6-linux-x86_64.egg/Cython/Build/Dependencies.py", line 1321, in cythonize_one
        raise CompileError(None, pyx_file)
    Cython.Compiler.Errors.CompileError: bcolz/carray_ext.pyx
    ----------------------------------------
ERROR: Command errored out with exit status 1: /home/nsambhu/anaconda3/envs/CAL/bin/python -u -c 'import io, os, sys, setuptools, tokenize; sys.argv[0] = '"'"'/tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/setup.py'"'"'; __file__='"'"'/tmp/pip-install-35fx6st2/bcolz_2cb00a558edc4855a37c1e7c2ad98ad7/setup.py'"'"';f = getattr(tokenize, '"'"'open'"'"', open)(__file__) if os.path.exists(__file__) else io.StringIO('"'"'from setuptools import setup; setup()'"'"');code = f.read().replace('"'"'\r\n'"'"', '"'"'\n'"'"');f.close();exec(compile(code, __file__, '"'"'exec'"'"'))' install --record /tmp/pip-record-_u238wl2/install-record.txt --single-version-externally-managed --compile --install-headers /home/nsambhu/anaconda3/envs/CAL/include/python3.6m/bcolz Check the logs for full command output.

failed

CondaEnvException: Pip failed
```
