//Some Solidity useful functions
pragma solidity ^0.4.11;
library StringUtil{
    
    event notConvertible(string);
    
    function stringToUint(string s) constant returns (uint result)  {
        bytes  bytes_num_reversed; 
        bytes memory b = bytes(s); // bytes reversed the string

        bool zero_out = false;
        result = 0;
        for(uint i=0; i< b.length; i++){
            uint hex_to_int = uint(b[i]);
            if(hex_to_int<48 || hex_to_int>57){
                notConvertible("The input string has value different than numbers!");
                throw;
            }
            else if (hex_to_int != 48){ //remove zeros in front
                 zero_out = true; // saying to stop removing zeros
                 bytes_num_reversed.push(b[i]);
            }
            else {
                if (zero_out){
                bytes_num_reversed.push(b[i]);
                }
            }
        }
        uint len = bytes_num_reversed.length;
        for(uint idx = 0; idx < len; idx++){
            result += (uint(bytes_num_reversed[idx])-48)*(10**(len-(idx+1)));
        }
        clearBytes(bytes_num_reversed);
    return result;
    }

    function clearBytes(bytes _input) private {
        for (uint i = 0; i < _input.length; i++){
            delete _input[i];
        }
    }
}
