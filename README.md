# AB-INITIO

FIND OUT HIGHEST VALUE USING ROLL UP AND SCAN
 
USING ROLL UP:

type temporary_type = record
decimal(“,”) count;
decimal(“,”) second;
end;

out::initialize(in) =begin
out.count :: 0;
out.second :: in.trans_amount;
end;

out::rollup(tmp, in) =begin 
out.count :: tmp.count+1;
out.second : : if(tmp.count == 1)in.trans_amount else tmp.second;
end;

out : : finalize(tmp, in) = begin
out.* : : in.*;  /**GENERATED*’in. *’* */
out.second : : tmp.second;
end;

USING SCAN:

output_select
if(count == 1) trans_amount
