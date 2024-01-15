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
~~winget install JanDeDobbeleer.ohmyposh~~
install-module -Name Terminal-Icons -Repositoritory PSGallery
notepad $profile
``````

add following in notepad, save and exit:
``````text
~~oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/quick-term.omp.json" | Invoke-Expression~~
Import-Module -Name Terminal-Icons
Clear-Host

function prompt {
	$lastCommand = Get-History -Count 1
	$commandTime = New-TimeSpan
	$today = Get-Date -Format "yyyy-MM-dd HH:mm"
	$wrkdir = pwd
	if($lastCommand){
		if($lastCommand.Duration.TotalMilliseconds -ge 1000){
			if($lastCommand.Duration.TotalMinutes -ge 1){
				# Minutes
				$commandTime = "Duration: {0}:{1}:{2} min > " -f  $lastCommand.Duration.Minutes, $lastCommand.Duration.Seconds, $lastCommand.Duration.Microseconds
			}else{
				# Seconds only
				$commandTime = "Duration: {0}:{1} sec > " -f $lastCommand.Duration.Seconds, $lastCommand.Duration.Microseconds
			}
		}else {
			# Milliseconds
			$commandTime = "Duration: {0}ms > " -f $lastCommand.Duration.Milliseconds 
		}
	}
	"┌  > $today > $wrkdir > $commandTime `n└┤=> "
}
``````
Reload profle with ``$profile`` or restart powershell.

That's it for now.
