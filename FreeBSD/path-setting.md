# Add private binary to path

1. Add the following code to the .cshrc

  ```shell
  # Include user's private bin directory if exists
  if ( -d "$HOME/.local/bin" ) then
      # Include only if $HOME/.local/bin was not in $path
      if ( "$path" !~ "*$HOME/.local/bin*" ) then
          set path = ("$HOME/.local/bin" $path)
      endif 
  endif

  # Include user's private bin directory if exists
  if ( -d "$HOME/bin" ) then
      # Include only if $HOME/bin was not in $path
      if ( "$path" !~ "*$HOME/bin*" ) then
          set path = ("$HOME/bin" $path)
      endif 
  endif
  ```
  
