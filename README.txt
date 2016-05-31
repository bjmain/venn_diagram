# venn_diagram

import matplotlib.pyplot as P
import matplotlib_venn as V


pplr = 0.8

#gene order is conserved in all tr files
genes = [line.strip().split()[1] for line in open("cyp1-T3-AE_S202.tr") if line[0]!="#"]

M_pplr = [float(line.strip().split()[0]) for line in open("Mopti.pplr") if line[0]!="#"]
M_pplr_ID = dict(zip(M_pplr,genes))
M_ID_pplr = dict(zip(genes, M_pplr))
 
cyp_pplr = [float(line.strip().split()[0]) for line in open("cyp1.pplr") if line[0]!="#"]
cyp_ID_pplr = dict(zip(genes, cyp_pplr))

Mlist=[]
for G in M_ID_pplr:
    if M_ID_pplr[G]>pplr:
        Mlist.append(G)

cyplist=[]
for gene in cyp_ID_pplr:
    if cyp_ID_pplr[gene]>pplr:
        cyplist.append(gene)

#make sets
M = set(Mlist)
CYP = set(cyplist)

V.venn2([M, CYP], ('M', 'cyp'))
P.title("Overexpressed genes ({} pplr) in response to permethrin stress".format(pplr))
P.show()
