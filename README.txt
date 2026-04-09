HUFFMAN PAGE COMPRESSION — PROJECT FILES
=========================================

FILES:
  dictionary.py   — inbuilt Huffman codebook (341 words, not counted in size)
  layout.py       — fixed page/grid constants (A4, line-height boxes)
  encoder.py      — text -> matrix of [x, 0, z, huffman_code]
  decoder.py      — matrix -> reconstructed text
  analyse.py      — runs test cases and shows full size breakdown

SAMPLE INPUTS:
  one_page.txt    — ~250 words
  five_pages.txt  — ~1250 words
  twenty_pages.txt— ~5000 words

HOW TO RUN:
  python encoder.py one_page.txt
  python decoder.py one_page_matrix.txt
  python analyse.py

MATRIX FORMAT:
  Page separator row : [page_number, 0, 0, 0]
  Word row           : [x, 0, z, huffman_code]
    x = horizontal pixel position within line-box (10 bits)
    y = always 0, omitted (line height fixed)
    z = line number on current page (6 bits)
    code = Huffman code from inbuilt dictionary (1-9 bits avg 6.5)

RESULTS (40 test cases, 1 to 10000 pages):
  Average space saved : 32.5%
  Compression ratio   : 67.5%
  Spread across all sizes : < 1% (scale-invariant)
