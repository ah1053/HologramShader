# HologramShader
Hologram Shader using Unity Shader Lab (Surface Shader - Lambert Lighting Model)


Car Hologram
Using Unity Shader Lab (HLSL(CG))
Implementing Rim Lighting Effect then Setting the Alpha to fade.

<img src="https://miro.medium.com/max/5744/1*vO8I3neBcpe4C7NlDeR9Aw.png" />
<br>
<img src="https://miro.medium.com/max/5752/1*S0zF_8GJsONdnVULtoBFRw.png" />
<br>
<img src="https://miro.medium.com/max/3020/1*Juew6__F6dMl1MRBZW-QqA.png" />
Fewer depth details Might be Produced by turning by Including a pass and getting the Z-Buffer calculation
<img src="https://miro.medium.com/max/5748/1*h9b3iyZbDTULigVqe9s5PQ.png" />


<br>
Hologram CG program
CGPROGRAM
<br>
    <code>
       
         #pragma surface surf Lambert alpha:fade
         #pragma target 3.0
 
         float4 _RimColor;
         half _RimRange;
         struct Input
         {
        
             float3 viewDir;
         };
 
         void surf (Input IN, inout SurfaceOutput o)
         {
             half rim=1- saturate(dot(normalize(IN.viewDir),o.Normal));
             o.Emission=_RimColor.rgb*pow(rim,_RimRange)*10;
             o.Alpha=pow(rim,_RimRange);
 
         }
         ENDCG
         </code>
For Turning Depth Details off use a pass before your CG Program
<br>
<code>
         Pass{
         ZWrite on
         ColorMask 0 }
 </code>

