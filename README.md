# Comandos Novo Linux (base CachyOs)

## Alterar teclado para abn2 | <small>(Se necessário)</small>

```
nano ~/.config/hypr/hyprland.conf
```

- Procure a área de INPUT e altere para: 
	- kb_layout = br
	- kb_model = abnt2

## Comandos inicias

### Pegar o melhor mirror no CachyOs
```bash
sudo cachyos-rate-mirrors
``` 
### Atualizar sistema
```bash
sudo pacman -Syu
```
### Instalar Fish, yay
```bash
sudo pacman -S fish yay xdg-user-dirs os-prober docker docker-compose 
```
### Instalar Google Chrome
```bash
yay -S google-chrome
``` 

---
### Alterar nome das pastas principais

<small>
OBS: Se você instalou em português e as pastas estão em português e quer mudar pra inglês)
</small>

1 - Força a atualização dos caminhos para o padrão 'C' (Inglês) 
```bash
LC_ALL=C xdg-user-dirs-update --force
```

2 - Cria as pastas fisicamente caso o comando acima não as crie

```bash
mkdir -p ~/Desktop ~/Documents ~/Downloads ~/Music ~/Pictures ~/Videos ~/Public ~/Templates
```
3 - Mova os dados das pastas antigas
- Comando caso tenha algo dentro das pastas
```
for folder in Documentos:Documents Downloads:Downloads Imagens:Pictures Músicas:Music Vídeos:Videos Público:Public Modelos:Templates
    set split (string split ":" $folder)
    set old $split[1]
    set new $split[2]
    
    # Move os arquivos se a pasta antiga existir
    if test -d ~/$old
        mv ~/$old/* ~/$new/ 2>/dev/null
        rmdir ~/$old 2>/dev/null
    end
end
```
```bash
mv ~/Área\ de\ Trabalho/* ~/Desktop/ 2>/dev/null; rmdir ~/Área\ de\ Trabalho/ 2>/dev/null
```
	
- Comando caso não tenha nada dentro das pastas
```bash
rmdir ~/Documentos ~/Downloads ~/Imagens ~/Músicas ~/Vídeos ~/Público ~/Modelos ~/Área\ de\ Trabalho 2>/dev/null

```

### Fish como terminal padrão
```bash
chsh -s /usr/bin/fish
```

### Docker
```bash
sudo pacman -S docker docker-compose
```
```bash
sudo systemctl enable --now docker.service
```
```bash
sudo usermod -aG docker $USER
```
<small>Reinicie após finalizar</small>

---

## Adicionar Windows no Boot com Linux

-  Abre o arquivo de configuração
```bash
sudo nano /etc/default/grub
```

- Descomenta essa linha
```bash
    GRUB_DISABLE_OS_PROBER=false
``` 

- Atualizar o menu do grub
```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## Instalando End 4

- Clone o repo
```bash
git clone https://github.com/end-4/dots-hyprland.git && cd dots-hyprland && ./setup install
```
