# scripts

@echo off
title Limpeza automatica do Windows

echo ================================
echo  LIMPEZA DE FICHEIROS TEMPORARIOS
echo ================================
echo.

REM Limpar %TEMP%
echo A limpar %TEMP%...
del /f /s /q "%TEMP%\*.*" 2>nul
for /d %%i in ("%TEMP%\*") do rd /s /q "%%i" 2>nul

echo.
echo ================================
echo  LIMPEZA DE PREFETCH
echo ================================
echo.

REM Limpar Prefetch
echo A limpar C:\Windows\Prefetch...
del /f /s /q "C:\Windows\Prefetch\*.*" 2>nul
for /d %%i in ("C:\Windows\Prefetch\*") do rd /s /q "%%i" 2>nul

echo.
echo ================================
echo  LIMPEZA DE DISCO (cleanmgr)
echo ================================
echo.

REM Executar Cleanmgr
cleanmgr /sageset:1
cleanmgr /sagerun:1

echo.
echo Operacao concluida!
pause
