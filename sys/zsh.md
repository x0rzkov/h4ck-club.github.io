*remove color from output*
| sed -r "s,\x1B\[[0-9;]*[a-zA-Z],,g" 
