
 **Diffusion**
  --------------------------------------------------------
**[ Denoising Diffusion Probabilistic Models ]** 

1. backward process
	- noise에서 image로 가는 형태

2. forward process (Diffusion process)
	- image에서 noise로 가는 형태
	- Gaussian 분포에서 나온 noise를 더해주는 과정    
	  점차 원본 image는 Gaussian 분포에 가까워지게 됨
	- beta: step을 얼마나 촘촘히 가져가는지를 결정

3. Disadvantages
	- bit rate가 작은, 사람의 눈에 크게 중요해 보이지 않는 non perceptual한 부분을 학습하는데 초점을 두고 있음
	- 반면, AE는 bit rate가 비교적 큰 perceptual한 부분을 학습하는데 초점을 두고 있음
	- **이에 Stable Diffusion은 보다 perceptual한 부분에 초점을 맞춰 학습하는 diffusion model을 제안함**
	- 즉 pixel 값을 직접 예측하는 것이 아닌, AE로부터 압축된 latent embedding을 예측하는 방법

<br>  
<br>  

**[ Stable Diffusion: High-Resolution Image Synthesis with Latent Diffusion Models ]** 

1. Perceptual Image Compression
	- 기존의 AE 학습 방법과 동일하게 perceptual loss를 사용하여 이루어짐
	 
2. Latent Diffusion Models 
	- AE로 정보 압축 시에, high frequency와 사람 눈으로 인식 안되는 noise 정보들은 모두 제거
	- 이에 보다 semantic 한 부분에 집중할 수 있으며, 계산 복잡도는 현저히 줄어듦

3. Decoder
	- step마다 UNet을 학습시키는 구조

5. Conditioning Mechansisms
	-  1가지 condition을 입력으로 받으며, 
	   각 condition은 적절한 encoder가 필요함 <br>
	   ex) text condition -> pretrained LLM의 text encoder
	- 입력된 condition y와 image 정보 z의 상관 관계를 고려하기 위해 cross attention 사용
	  이후, 가중치가 반영된 condition y가 z에 더해짐
	 
