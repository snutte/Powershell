# Current modules, addons and programs
* Oh-My-Posh
  * Quick-Term
* Terminal-Icons
* Nerd-Fonts/DejaVuSansMono
* Nvim
## Copy paste notes
Font download and install: https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/DejaVuSansMono.zip

In powershell:
``````
winget install Neovim.Neovim
winget install JanDeDobbeleer.ohmyposh
install-module -Name Terminal-Icons -Repositoritory PSGallery
notepad $profile
``````

add following in notepad, save and exit:
``````text
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/quick-term.omp.json" | Invoke-Expression
import-module Terminal-Icons
``````
Reload profle with ``$profile`` or restart powershell.

That's it for now.
