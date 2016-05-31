# venn_diagram

import matplotlib_venn as V
import matplotlib.pyplot as P

set1 = set(['A', 'B', 'C', 'D'])
set2 = set(['B', 'C', 'D', 'E'])
V.venn2([set1, set2], ('Set1', 'Set2'))

P.show()

