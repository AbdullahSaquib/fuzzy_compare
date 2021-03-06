# Simple Fuzzy Comparison
Calculating how much two strings are similar to each other by analysing the number of common and uncommon characters in the two strings. The algorithm used has time complexity O(n+m), where n and m are the lengths of the compared words. It uses two lists to keep track of the number of times a character is present in each word and later uses them to calculate the final matching score between 0 and 1, where 1 represents complete match and 0 represents no match.

## Installation

    pip install fuzzy_compare

## How To Use
    from fuzzy_compare import compare_english_words
    
    print(compare_english_words("hello", "hello"))  # Out: 1.0
    print(compare_english_words("hello", "helllo"))  # Out: 0.9090...
    print(compare_english_words("hello", "hell"))  # Out: 0.888...
    print(compare_english_words("hello", "hallo"))  # Out: 0.8
    print(compare_english_words("hello", "world"))  # Out: 0.4
    print(compare_english_words("hello", ""))  # Out: 0.0

## Support For Other Languages
The algorithm allows to compare two strings containing any python supported characters. The compare_english_words function only keeps track of the Unicode characters with code range between 97 and 122, because 97 is unicode of 'a' and 122 of 'z'.

    from fuzzy_compare import CompareStrings
    
    _eng_words_comp_obj = CompareStrings(97, 122)
    compare_english_words = _eng_words_comp_obj.compare_strings
    print(compare_english_words("hello", "world"))  # Out: 0.4

The class CompareStrings can be used to compare strings containing any unicode characters in any given code range. But, remember that the algorithm maintains two lists of length equal to the range of allowed Unicode characters. In case of compare_english_words, two lists of length 26 each are used to keep track of the character count.