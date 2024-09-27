Here we present a direct way by use of Magma to compute a canonical model for a quotient modular curve
and after having it, call to the Automorphism instruction on Magma in order to compute its automorphism group.

We deal this with the example of $X_0(115)/\langle w_{23}\rangle$.


## Example


````magma

M := ModularForms(115,2);
S := CuspidalSubspace(M);
//Dimension(S);
B:=Basis(S);
W := AtkinLehnerOperator(S, 23);
//W;
//Eigenvalues(W);
//Eigenspace(W, 1);
F:=[(B[1] - B[7] + B[10]),
    (2*B[2] - 6*B[7] + 2*B[9] + B[10] - 2*B[11]),
    (B[2] + B[3] - 2*B[7] - 2*B[8] + B[9] + B[10] - 2*B[11]),
    (-B[2] + B[4] + 3*B[7] - B[8] - B[9]),
    (B[5] + 2*B[7] + 2*B[8] - 2*B[9] - B[10] + 2*B[11]),
    (B[6] - B[7] - B[8] + B[9])];
prec:=200;
L<q> := LaurentSeriesRing(Rationals(),prec);
R<[x]>:=PolynomialRing(Rationals(),6);
Bexp:=[L!qExpansion(f,prec): f in F];
eqns:=[R | ];
	d:=1;
tf:=false;
	while tf eq false do
		d:=d+1;
		mons:=MonomialsOfDegree(R,d);
		monsq:=[Evaluate(mon,Bexp) : mon in mons];
		V:=VectorSpace(Rationals(),#mons);
		W:=VectorSpace(Rationals(),prec-10);
		h:=hom<V->W | [W![Coefficient(monsq[i],j) : j in [1..(prec-10)]] : i in [1..#mons]]>;
		K:=Kernel(h);
		eqns:=eqns cat [ &+[Eltseq(V!k)[j]*mons[j] : j in [1..#mons] ] : k in Basis(K)  ];
		X:=Scheme(ProjectiveSpace(R),eqns);
		if Dimension(X) eq 1 then
			if IsSingular(X) eq false then
				X:=Curve(ProjectiveSpace(R),eqns);
				if Genus(X) eq 6 then
					tf:=true;
				end if;
			end if;
		end if;
	end while;
eqns:=GroebnerBasis(ideal<R | eqns>); // Simplifying the equations.
	tf:=true;
	repeat
		t:=#eqns;
		tf:=(eqns[t] in ideal<R | eqns[1..(t-1)]>);
		if tf then 
			Exclude(~eqns,eqns[t]);
		end if;
	until tf eq false;
	t:=0;
	repeat
		t:=t+1;
		tf:=(eqns[t] in ideal<R | Exclude(eqns,eqns[t])>);	
		if tf then
			Exclude(~eqns,eqns[t]);
			t:=0;
		end if;
        until tf eq false;
t:=0;
	repeat
		t:=t+1;
		tf:=(eqns[t] in ideal<R | Exclude(eqns,eqns[t])>);	
		if tf then
			Exclude(~eqns,eqns[t]);
			t:=0;
		end if;
	until tf eq false and t eq #eqns;
X:=Curve(ProjectiveSpace(R),eqns);
//X;


````````````````
Y:=ChangeRing(X,GF(2));
if IsSingular(Y) eq false then
#Automorphisms(Y);
end if;
