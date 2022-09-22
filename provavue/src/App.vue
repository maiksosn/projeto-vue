<template>
  <div class="main" id="app">
    <div class="col-md-6 offset-md-1">
      <h3 class="box_header dados_pessoais">Dados Pessoais</h3>
    </div>
    <form>
      <div class="col-md-6 offset-md-1 nome">
        <label for="nome">Nome</label> <br />
        <input
          v-model="nome"
          v-bind:class="{
            'form-control': true,
            'is-invalid': !validaNome(nome) && nameBlured,
            'is-valid': validaNome(nome),
          }"
          v-on:blur="nameBlured = true"
        />
        <div class="invalid-feedback">
          "Nome completo" não pode ficar em branco.
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 email">
            <label for="email">E-mail</label>
            <input
              v-model="email"
              v-bind:class="{
                'form-control': true,
                'is-invalid': !validaEmail(email) && emailBlured,
                'is-valid': validaEmail(email),
              }"
              v-on:blur="emailBlured = true"
            />
            <div class="invalid-feedback">
              <span> "E-mail" não pode ficar em branco.</span>
            </div>
          </div>
          <div class="col-md-6 mt-5 senha">
            <label for="senha">Senha</label>
            <input
              v-model="senha"
              v-bind:class="{
                'form-control': true,
                'is-invalid': !validaSenha(senha) && senhaBlured,
                'is-valid': validaSenha(senha),
              }"
              v-on:blur="senhaBlured = true"
            />
          </div>
          <div class="invalid-feedback">
            <span> "Senha" não pode ficar em branco.</span>
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 dtns">
            <label for="dtns">Data Nascimento</label>
            <input
              v-model="dtns"
              v-bind:class="{
                'form-control': true,
                'is-invalid': !validaDtns(dtns) && dtnsBlured,
                'is-valid': validaDtns(dtns),
              }"
              v-on:blur="dtnsBlured = true"
            />
            <div class="invalid-feedback">
              <span> "Data Nascimento" não pode ficar em branco.</span>
            </div>
          </div>

          <div class="col-md-6 mt-5 cpf">
            <label for="cpf">CPF</label>
            <input
              v-model="cpf"
              v-bind:class="{
                'form-control': true,
                'is-invalid': !validaCpf(cpf) && cpfBlured,
                'is-valid': validaCpf(cpf),
              }"
              v-on:blur="cpfBlured = true"
            />
            <div class="invalid-feedback">
              <span> "CPF" não pode ficar em branco.</span>
            </div>
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 pfd">
            <label for="curriculum-children"
              >Possui filhos ou dependentes?</label
            >
            <select
              id="curriculum-children"
              class="form-control form-select border-dark"
              name="Curriculum[children]"
            >
              <option value="">Selecione</option>
              <option value="0">Não</option>
              <option value="1">Sim</option>
            </select>
          </div>

          <div class="col-md-6 mt-5 qfd">
            <label for="curriculum-children"
              >Quantos filhos ou dependentes?</label
            >
            <select
              id="curriculum-children"
              class="form-control form-select border-dark"
              name="Curriculum[children]"
            >
              <option value="">Selecione</option>
              <option value="0">Não</option>
              <option value="1">Sim</option>
            </select>
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 ec">
            <label for="curriculum-children">Estado cívil</label>
            <select
              id="curriculum-children"
              class="form-control form-select border-dark"
              name="Curriculum[children]"
            >
              <option value="">Selecione</option>
              <option value="0">Casado</option>
              <option value="1">divorciado</option>
              <option value="2">solteiro</option>
              <option value="3">viuvo</option>
            </select>
          </div>

          <div class="col-md-6 mt-5 sx">
            <label for="curriculum-children">Sexo</label>
            <select
              id="curriculum-children"
              class="form-control form-select border-dark"
              name="Curriculum[children]"
            >
              <option value="">Selecione</option>
              <option value="0">Masculino</option>
              <option value="1">Feminino</option>
            </select>
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 pd">
            <label for="curriculum-children">Possui deficiência?</label>
            <select
              id="curriculum-children"
              class="form-control form-select border-dark"
              name="Curriculum[children]"
            >
              <option value="">Selecione</option>
              <option value="0">Não</option>
              <option value="1">Sim</option>
            </select>
          </div>
          <div class="col-md-6 mt-5 qd">
            <label for="curriculum-children">Qual deficiência?</label>
            <select
              id="curriculum-children"
              class="form-control form-select border-dark"
              name="Curriculum[children]"
            >
              <option value="">Selecione</option>
              <option value="0">Auditiva</option>
              <option value="1">Física</option>
              <option value="2">Intelectual</option>
              <option value="3">Mental</option>
              <option value="4">Múltipla</option>
              <option value="5">Outra</option>
              <option value="6">Visual</option>
            </select>
          </div>
        </div>
      </div>

      <div class="col-md-4 offset-md-1">
        <div class="col-md-4 mt-5 cep">
          <label for="cep">Cep</label> <br />
          <input
            class="form-control border border-dark"
            type="text"
            v-model="cep"
            @keyup="searchCep()"
          />
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-8 mt-5 endereco">
            <label for="endereco">Endereço</label>
            <input
              class="form-control border-dark"
              type="text"
              name="endereco"
              id="logradouro"
            />
          </div>
          <div class="col-md-4 mt-5 numero">
            <label for="numero">Número</label>
            <input
              class="form-control border-dark"
              type="text"
              name="numero"
              id="numero"
            />
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 bairro">
            <label for="bairro">Bairro</label>
            <input
              class="form-control border-dark"
              type="text"
              name="bairro"
              id="bairro"
            />
          </div>
          <div class="col-md-6 mt-5 complemento">
            <label for="complemento">Complemento</label>
            <input
              class="form-control border-dark"
              type="text"
              name="complemento"
              id="complemento"
            />
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 cidades">
            <label for="localidade">Cidades</label>
            <select
              id="localidade"
              class="form-control form-select border-dark"
              name="localidade"
              placeholder="Localidade"
            >
              <option value="">Selecione</option>
              <option value="3911">Abatiá</option>
              <option value="3912">Adrianópolis</option>
              <option value="3913">Agudos do Sul</option>
              <option value="3914">Almirante Tamandaré</option>
              <option value="3915">Altamira do Paraná</option>
              <option value="4305">Alto Paraíso</option>
              <option value="3917">Alto Paraná</option>
              <option value="3918">Alto Piquiri</option>
              <option value="3916">Altônia</option>
              <option value="3919">Alvorada do Sul</option>
              <option value="3920">Amaporã</option>
              <option value="3921">Ampére</option>
              <option value="3922">Anahy</option>
              <option value="3923">Andirá</option>
              <option value="3924">Ângulo</option>
              <option value="3925">Antonina</option>
              <option value="3926">Antônio Olinto</option>
              <option value="3927">Apucarana</option>
              <option value="3928">Arapongas</option>
              <option value="3929">Arapoti</option>
              <option value="3930">Arapuã</option>
              <option value="3931">Araruna</option>
              <option value="3932">Araucária</option>
              <option value="3933">Ariranha do Ivaí</option>
              <option value="3934">Assaí</option>
              <option value="3935">Assis Chateaubriand</option>
              <option value="3936">Astorga</option>
              <option value="3937">Atalaia</option>
              <option value="3938">Balsa Nova</option>
              <option value="3939">Bandeirantes</option>
              <option value="3940">Barbosa Ferraz</option>
              <option value="3942">Barra do Jacaré</option>
              <option value="3941">Barracão</option>
              <option value="3943">Bela Vista da Caroba</option>
              <option value="3944">Bela Vista do Paraíso</option>
              <option value="3945">Bituruna</option>
              <option value="3946">Boa Esperança</option>
              <option value="3947">Boa Esperança do Iguaçu</option>
              <option value="3948">Boa Ventura de São Roque</option>
              <option value="3949">Boa Vista da Aparecida</option>
              <option value="3950">Bocaiúva do Sul</option>
              <option value="3951">Bom Jesus do Sul</option>
              <option value="3952">Bom Sucesso</option>
              <option value="3953">Bom Sucesso do Sul</option>
              <option value="3954">Borrazópolis</option>
              <option value="3955">Braganey</option>
              <option value="3956">Brasilândia do Sul</option>
              <option value="3957">Cafeara</option>
              <option value="3958">Cafelândia</option>
              <option value="3959">Cafezal do Sul</option>
              <option value="3960">Califórnia</option>
              <option value="3961">Cambará</option>
              <option value="3962">Cambé</option>
              <option value="3963">Cambira</option>
              <option value="3964">Campina da Lagoa</option>
              <option value="3965">Campina do Simão</option>
              <option value="3966">Campina Grande do Sul</option>
              <option value="3967">Campo Bonito</option>
              <option value="3968">Campo do Tenente</option>
              <option value="3969">Campo Largo</option>
              <option value="3970">Campo Magro</option>
              <option value="3971">Campo Mourão</option>
              <option value="3972">Cândido de Abreu</option>
              <option value="3973">Candói</option>
              <option value="3974">Cantagalo</option>
              <option value="3975">Capanema</option>
              <option value="3976">Capitão Leônidas Marques</option>
              <option value="3977">Carambeí</option>
              <option value="3978">Carlópolis</option>
              <option value="3979">Cascavel</option>
              <option value="3980">Castro</option>
              <option value="3981">Catanduvas</option>
              <option value="3982">Centenário do Sul</option>
              <option value="3983">Cerro Azul</option>
              <option value="3984">Céu Azul</option>
              <option value="3985">Chopinzinho</option>
              <option value="3986">Cianorte</option>
              <option value="3987">Cidade Gaúcha</option>
              <option value="3988">Clevelândia</option>
              <option value="3989">Colombo</option>
              <option value="3990">Colorado</option>
              <option value="3991">Congonhinhas</option>
              <option value="3992">Conselheiro Mairinck</option>
              <option value="3993">Contenda</option>
              <option value="3994">Corbélia</option>
              <option value="3995">Cornélio Procópio</option>
              <option value="3996">Coronel Domingos Soares</option>
              <option value="3997">Coronel Vivida</option>
              <option value="3998">Corumbataí do Sul</option>
              <option value="4002">Cruz Machado</option>
              <option value="3999">Cruzeiro do Iguaçu</option>
              <option value="4000">Cruzeiro do Oeste</option>
              <option value="4001">Cruzeiro do Sul</option>
              <option value="4003">Cruzmaltina</option>
              <option value="4004">Curitiba</option>
              <option value="4005">Curiúva</option>
              <option value="4008">Diamante D'oeste</option>
              <option value="4006">Diamante do Norte</option>
              <option value="4007">Diamante do Sul</option>
              <option value="4009">Dois Vizinhos</option>
              <option value="4010">Douradina</option>
              <option value="4011">Doutor Camargo</option>
              <option value="4306">Doutor Ulysses</option>
              <option value="4012">Enéas Marques</option>
              <option value="4013">Engenheiro Beltrão</option>
              <option value="4015">Entre Rios do Oeste</option>
              <option value="4014">Esperança Nova</option>
              <option value="4016">Espigão Alto do Iguaçu</option>
              <option value="4017">Farol</option>
              <option value="4018">Faxinal</option>
              <option value="4019">Fazenda Rio Grande</option>
              <option value="4020">Fênix</option>
              <option value="4021">Fernandes Pinheiro</option>
              <option value="4022">Figueira</option>
              <option value="4024">Flor da Serra do Sul</option>
              <option value="4023">Floraí</option>
              <option value="4025">Floresta</option>
              <option value="4026">Florestópolis</option>
              <option value="4027">Flórida</option>
              <option value="4028">Formosa do Oeste</option>
              <option value="4029">Foz do Iguaçu</option>
              <option value="4032">Foz do Jordão</option>
              <option value="4030">Francisco Alves</option>
              <option value="4031">Francisco Beltrão</option>
              <option value="4033">General Carneiro</option>
              <option value="4034">Godoy Moreira</option>
              <option value="4035">Goioerê</option>
              <option value="4036">Goioxim</option>
              <option value="4037">Grandes Rios</option>
              <option value="4038">Guaíra</option>
              <option value="4039">Guairaçá</option>
              <option value="4040">Guamiranga</option>
              <option value="4041">Guapirama</option>
              <option value="4042">Guaporema</option>
              <option value="4043">Guaraci</option>
              <option value="4044">Guaraniaçu</option>
              <option value="4045">Guarapuava</option>
              <option value="4046">Guaraqueçaba</option>
              <option value="4047">Guaratuba</option>
              <option value="4048">Honório Serpa</option>
              <option value="4049">Ibaiti</option>
              <option value="4050">Ibema</option>
              <option value="4051">Ibiporã</option>
              <option value="4052">Icaraíma</option>
              <option value="4053">Iguaraçu</option>
              <option value="4054">Iguatu</option>
              <option value="4055">Imbaú</option>
              <option value="4056">Imbituva</option>
              <option value="4057">Inácio Martins</option>
              <option value="4058">Inajá</option>
              <option value="4059">Indianópolis</option>
              <option value="4060">Ipiranga</option>
              <option value="4061">Iporã</option>
              <option value="4062">Iracema do Oeste</option>
              <option value="4063">Irati</option>
              <option value="4064">Iretama</option>
              <option value="4065">Itaguajé</option>
              <option value="4066">Itaipulândia</option>
              <option value="4067">Itambaracá</option>
              <option value="4068">Itambé</option>
              <option value="4069">Itapejara D'oeste</option>
              <option value="4070">Itaperuçu</option>
              <option value="4071">Itaúna do Sul</option>
              <option value="4072">Ivaí</option>
              <option value="4073">Ivaiporã</option>
              <option value="4074">Ivaté</option>
              <option value="4075">Ivatuba</option>
              <option value="4076">Jaboti</option>
              <option value="4077">Jacarezinho</option>
              <option value="4078">Jaguapitã</option>
              <option value="4079">Jaguariaíva</option>
              <option value="4080">Jandaia do Sul</option>
              <option value="4081">Janiópolis</option>
              <option value="4082">Japira</option>
              <option value="4083">Japurá</option>
              <option value="4084">Jardim Alegre</option>
              <option value="4085">Jardim Olinda</option>
              <option value="4086">Jataizinho</option>
              <option value="4087">Jesuítas</option>
              <option value="4088">Joaquim Távora</option>
              <option value="4089">Jundiaí do Sul</option>
              <option value="4090">Juranda</option>
              <option value="4091">Jussara</option>
              <option value="4092">Kaloré</option>
              <option value="4093">Lapa</option>
              <option value="4094">Laranjal</option>
              <option value="4095">Laranjeiras do Sul</option>
              <option value="4096">Leópolis</option>
              <option value="4097">Lidianópolis</option>
              <option value="4098">Lindoeste</option>
              <option value="4099">Loanda</option>
              <option value="4100">Lobato</option>
              <option value="4101">Londrina</option>
              <option value="4102">Luiziana</option>
              <option value="4103">Lunardelli</option>
              <option value="4104">Lupionópolis</option>
              <option value="4105">Mallet</option>
              <option value="4106">Mamborê</option>
              <option value="4107">Mandaguaçu</option>
              <option value="4108">Mandaguari</option>
              <option value="4109">Mandirituba</option>
              <option value="4110">Manfrinópolis</option>
              <option value="4111">Mangueirinha</option>
              <option value="4112">Manoel Ribas</option>
              <option value="4113">Marechal Cândido Rondon</option>
              <option value="4114">Maria Helena</option>
              <option value="4115">Marialva</option>
              <option value="4116">Marilândia do Sul</option>
              <option value="4117">Marilena</option>
              <option value="4118">Mariluz</option>
              <option value="4119">Maringá</option>
              <option value="4120">Mariópolis</option>
              <option value="4121">Maripá</option>
              <option value="4122">Marmeleiro</option>
              <option value="4123">Marquinho</option>
              <option value="4124">Marumbi</option>
              <option value="4125">Matelândia</option>
              <option value="4126">Matinhos</option>
              <option value="4127">Mato Rico</option>
              <option value="4128">Mauá da Serra</option>
              <option value="4129">Medianeira</option>
              <option value="4130">Mercedes</option>
              <option value="4131">Mirador</option>
              <option value="4132">Miraselva</option>
              <option value="4133">Missal</option>
              <option value="4134">Moreira Sales</option>
              <option value="4135">Morretes</option>
              <option value="4136">Munhoz de Melo</option>
              <option value="4137">Nossa Senhora das Graças</option>
              <option value="4138">Nova Aliança do Ivaí</option>
              <option value="4139">Nova América da Colina</option>
              <option value="4140">Nova Aurora</option>
              <option value="4141">Nova Cantu</option>
              <option value="4142">Nova Esperança</option>
              <option value="4143">Nova Esperança do Sudoeste</option>
              <option value="4144">Nova Fátima</option>
              <option value="4145">Nova Laranjeiras</option>
              <option value="4146">Nova Londrina</option>
              <option value="4147">Nova Olímpia</option>
              <option value="4150">Nova Prata do Iguaçu</option>
              <option value="4148">Nova Santa Bárbara</option>
              <option value="4149">Nova Santa Rosa</option>
              <option value="4151">Nova Tebas</option>
              <option value="4152">Novo Itacolomi</option>
              <option value="4153">Ortigueira</option>
              <option value="4154">Ourizona</option>
              <option value="4155">Ouro Verde do Oeste</option>
              <option value="4156">Paiçandu</option>
              <option value="4157">Palmas</option>
              <option value="4158">Palmeira</option>
              <option value="4159">Palmital</option>
              <option value="4160">Palotina</option>
              <option value="4161">Paraíso do Norte</option>
              <option value="4162">Paranacity</option>
              <option value="4163">Paranaguá</option>
              <option value="4164">Paranapoema</option>
              <option value="4165">Paranavaí</option>
              <option value="4166">Pato Bragado</option>
              <option value="4167">Pato Branco</option>
              <option value="4168">Paula Freitas</option>
              <option value="4169">Paulo Frontin</option>
              <option value="4170">Peabiru</option>
              <option value="4171">Perobal</option>
              <option value="4172">Pérola</option>
              <option value="4173">Pérola D'oeste</option>
              <option value="4174">Piên</option>
              <option value="4175">Pinhais</option>
              <option value="4177">Pinhal de São Bento</option>
              <option value="4176">Pinhalão</option>
              <option value="4178">Pinhão</option>
              <option value="4179">Piraí do Sul</option>
              <option value="4180">Piraquara</option>
              <option value="4181">Pitanga</option>
              <option value="4182">Pitangueiras</option>
              <option value="4183">Planaltina do Paraná</option>
              <option value="4184">Planalto</option>
              <option value="4185">Ponta Grossa</option>
              <option value="4186">Pontal do Paraná</option>
              <option value="4187">Porecatu</option>
              <option value="4188">Porto Amazonas</option>
              <option value="4189">Porto Barreiro</option>
              <option value="4190">Porto Rico</option>
              <option value="4191">Porto Vitória</option>
              <option value="4192">Prado Ferreira</option>
              <option value="4193">Pranchita</option>
              <option value="4194">Presidente Castelo Branco</option>
              <option value="4195">Primeiro de Maio</option>
              <option value="4196">Prudentópolis</option>
              <option value="4197">Quarto Centenário</option>
              <option value="4198">Quatiguá</option>
              <option value="4199">Quatro Barras</option>
              <option value="4200">Quatro Pontes</option>
              <option value="4201">Quedas do Iguaçu</option>
              <option value="4202">Querência do Norte</option>
              <option value="4203">Quinta do Sol</option>
              <option value="4204">Quitandinha</option>
              <option value="4205">Ramilândia</option>
              <option value="4206">Rancho Alegre</option>
              <option value="4207">Rancho Alegre D'oeste</option>
              <option value="4208">Realeza</option>
              <option value="4209">Rebouças</option>
              <option value="4210">Renascença</option>
              <option value="4211">Reserva</option>
              <option value="4212">Reserva do Iguaçu</option>
              <option value="4213">Ribeirão Claro</option>
              <option value="4214">Ribeirão do Pinhal</option>
              <option value="4215">Rio Azul</option>
              <option value="4216">Rio Bom</option>
              <option value="4217">Rio Bonito do Iguaçu</option>
              <option value="4218">Rio Branco do Ivaí</option>
              <option value="4219">Rio Branco do Sul</option>
              <option value="4220">Rio Negro</option>
              <option value="4221">Rolândia</option>
              <option value="4222">Roncador</option>
              <option value="4223">Rondon</option>
              <option value="4224">Rosário do Ivaí</option>
              <option value="4225">Sabáudia</option>
              <option value="4226">Salgado Filho</option>
              <option value="4227">Salto do Itararé</option>
              <option value="4228">Salto do Lontra</option>
              <option value="4229">Santa Amélia</option>
              <option value="4230">Santa Cecília do Pavão</option>
              <option value="4231">Santa Cruz de Monte Castelo</option>
              <option value="4232">Santa Fé</option>
              <option value="4233">Santa Helena</option>
              <option value="4234">Santa Inês</option>
              <option value="4235">Santa Isabel do Ivaí</option>
              <option value="4236">Santa Izabel do Oeste</option>
              <option value="4237">Santa Lúcia</option>
              <option value="4238">Santa Maria do Oeste</option>
              <option value="4239">Santa Mariana</option>
              <option value="4240">Santa Mônica</option>
              <option value="4242">Santa Tereza do Oeste</option>
              <option value="4243">Santa Terezinha de Itaipu</option>
              <option value="4241">Santana do Itararé</option>
              <option value="4244">Santo Antônio da Platina</option>
              <option value="4245">Santo Antônio do Caiuá</option>
              <option value="4246">Santo Antônio do Paraíso</option>
              <option value="4247">Santo Antônio do Sudoeste</option>
              <option value="4248">Santo Inácio</option>
              <option value="4249">São Carlos do Ivaí</option>
              <option value="4250">São Jerônimo da Serra</option>
              <option value="4251">São João</option>
              <option value="4252">São João do Caiuá</option>
              <option value="4253">São João do Ivaí</option>
              <option value="4254">São João do Triunfo</option>
              <option value="4255">São Jorge D'oeste</option>
              <option value="4256">São Jorge do Ivaí</option>
              <option value="4257">São Jorge do Patrocínio</option>
              <option value="4258">São José da Boa Vista</option>
              <option value="4259">São José das Palmeiras</option>
              <option value="4260">São José dos Pinhais</option>
              <option value="4261">São Manoel do Paraná</option>
              <option value="4262">São Mateus do Sul</option>
              <option value="4263">São Miguel do Iguaçu</option>
              <option value="4264">São Pedro do Iguaçu</option>
              <option value="4265">São Pedro do Ivaí</option>
              <option value="4266">São Pedro do Paraná</option>
              <option value="4267">São Sebastião da Amoreira</option>
              <option value="4268">São Tomé</option>
              <option value="4269">Sapopema</option>
              <option value="4270">Sarandi</option>
              <option value="4271">Saudade do Iguaçu</option>
              <option value="4272">Sengés</option>
              <option value="4273">Serranópolis do Iguaçu</option>
              <option value="4274">Sertaneja</option>
              <option value="4275">Sertanópolis</option>
              <option value="4276">Siqueira Campos</option>
              <option value="4277">Sulina</option>
              <option value="4278">Tamarana</option>
              <option value="4279">Tamboara</option>
              <option value="4280">Tapejara</option>
              <option value="4281">Tapira</option>
              <option value="4282">Teixeira Soares</option>
              <option value="4283">Telêmaco Borba</option>
              <option value="4284">Terra Boa</option>
              <option value="4285">Terra Rica</option>
              <option value="4286">Terra Roxa</option>
              <option value="4287">Tibagi</option>
              <option value="4288">Tijucas do Sul</option>
              <option value="4289">Toledo</option>
              <option value="4290">Tomazina</option>
              <option value="4291">Três Barras do Paraná</option>
              <option value="4292">Tunas do Paraná</option>
              <option value="4293">Tuneiras do Oeste</option>
              <option value="4294">Tupãssi</option>
              <option value="4295">Turvo</option>
              <option value="4296">Ubiratã</option>
              <option value="4297">Umuarama</option>
              <option value="4298">União da Vitória</option>
              <option value="4299">Uniflor</option>
              <option value="4300">Uraí</option>
              <option value="4302">Ventania</option>
              <option value="4303">Vera Cruz do Oeste</option>
              <option value="4304">Verê</option>
              <option value="4307">Virmond</option>
              <option value="4308">Vitorino</option>
              <option value="4301">Wenceslau Braz</option>
              <option value="4309">Xambrê</option>
            </select>
          </div>
          <div class="col-md-6 mt-5 estados">
            <label for="uf">Estados</label>
            <select
              id="uf"
              class="form-control form-select border-dark"
              name="uf"
            >
              <option value="">Selecione</option>
              <option value="AC">Acre</option>
              <option value="AL">Alagoas</option>
              <option value="AP">Amapá</option>
              <option value="AM">Amazonas</option>
              <option value="BA">Bahia</option>
              <option value="CE">Ceará</option>
              <option value="DF">Distrito Federal</option>
              <option value="ES">Espírito Santo</option>
              <option value="GO">Goiás</option>
              <option value="MA">Maranhão</option>
              <option value="MT">Mato Grosso</option>
              <option value="MS">Mato Grosso do Sul</option>
              <option value="MG">Minas Gerais</option>
              <option value="PA">Pará</option>
              <option value="PB">Paraíba</option>
              <option value="PR">Paraná</option>
              <option value="PE">Pernambuco</option>
              <option value="PI">Piauí</option>
              <option value="RJ">Rio de Janeiro</option>
              <option value="RN">Rio Grande do Norte</option>
              <option value="RS">Rio Grande do Sul</option>
              <option value="RO">Rondônia</option>
              <option value="RR">Roraima</option>
              <option value="SC">Santa Catarina</option>
              <option value="SP">São Paulo</option>
              <option value="SE">Sergipe</option>
              <option value="TO">Tocantins</option>
              <option value="EX">Estrangeiro</option>
            </select>
          </div>
        </div>
      </div>

      <br />

      <div class="col-md-6 offset-md-1 tf">
        <label for="telefone">Telefone residencial</label>
        <input
          type="text"
          id="telefone"
          class="form-control border-dark"
          name="telefone"
        />
      </div>

      <br />

      <div class="col-md-6 offset-md-1 tc">
        <label for="telefone_contato">Telefone de contato</label>
        <input
          type="text"
          id="telefone_contato"
          class="form-control border-dark"
          name="telefone_contato"
        />
      </div>

      <br />

      <div class="col-md-6 offset-md-1 ramal">
        <label for="ramal">Ramal</label>
        <input
          type="text"
          id="ramal"
          class="form-control border-dark"
          name="ramal"
        />
      </div>

      <br />

      <div class="col-md-6 offset-md-1 telefone_celular">
        <label for="telefone_celular">Telefone Celular</label>
        <input
          type="text"
          id="telefone_celular"
          class="form-control border-dark"
          name="telefone_celular"
        />
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5 ad">
            <label for="deficiencia">Alguma Deficiencia ?</label>
            <select
              id="deficiencia"
              class="form-control form-select border-dark"
              name="deficiencia"
            >
              <option value="">Selecione</option>
              <option value="1">Sim</option>
              <option value="2">Não</option>
            </select>
          </div>
          <div class="col-md-6 mt-5 qd">
            <label for="email">Qual deficiencia</label>
            <input
              type="text"
              id="email"
              class="form-control border-dark"
              name="email"
            />
          </div>
        </div>
      </div>

      <br />

      <div class="col-md-6 offset-md-1">
        <h3 class="box_header">Formação Complementar</h3>
      </div>

      <div id="clone">
        <div class="col-md-6 offset-md-1">
          <h4
            class="box_header font-weight-bolder text-smalt-blue text-uppercase"
          >
            Curso <span id="count">01</span>
          </h4>
        </div>

        <div class="col-md-6 offset-md-1">
          <div class="row">
            <div class="col-md-6 mt-5">
              <label class="mb-1">Formação</label>
              <div class="mb-3">
                <select class="form-select">
                  <option value="">Selecione</option>
                  <option value="2">1º Grau (5º a 9º Série)</option>
                  <option value="3">2º Grau (1º a 3º Ano)</option>
                  <option value="5">3º Grau (Graduação)</option>
                  <option value="1">Ensino Fundamental (1º a 4º Série)</option>
                  <option value="9">Pós Graduação (Doutorado)</option>
                  <option value="6">Pós Graduação (Especialização)</option>
                  <option value="7">Pós Graduação (MBA)</option>
                  <option value="8">Pós Graduação (Mestrado)</option>
                </select>
              </div>
            </div>

            <div class="col-md-6 mt-5">
              <label>Curso</label>
              <br />
              <input v-model="message" class="form-control" />
            </div>
          </div>
        </div>

        <div class="col-md-6 offset-md-1">
          <div class="row">
            <div class="col-md-6 mt-5">
              <label class="mb-1">Situação do Curso</label>
              <div class="mb-3">
                <select class="form-select">
                  <option value="">Selecione</option>
                  <option value="1">Concluído</option>
                  <option value="2">Cursando</option>
                  <option value="3">Trancado</option>
                </select>
              </div>
            </div>
            <div class="col-md-6 mt-5">
              <label>Mês e Ano de conclusão</label>
              <br />
              <input v-model="message" class="form-control" />
            </div>
          </div>
        </div>

        <div class="col-md-6 offset-md-1">
          <div class="row">
            <div class="col-md-6 mt-5">
              <label class="mb-1">Turno</label>
              <div class="mb-3">
                <select class="form-select">
                  <option value="">Selecione</option>
                  <option value="M">Matutino</option>
                  <option value="V">Vespertino</option>
                  <option value="N">Noturno</option>
                  <option value="I">Integral</option>
                </select>
              </div>
            </div>
            <div class="col-md-6 mt-5">
              <label>Instituição</label>
              <br />
              <input v-model="message" class="form-control" />
            </div>
          </div>
        </div>
      </div>

      <div id="clone2"></div>

      <div class="col-md-6 offset-md-1">
        <div class="text-right col-md-12 mt-4">
          <button class="bg btn btn-primary" type="button" @click="Clone()">
            Formação Complementar +
          </button>
        </div>
      </div>

      <br />

      <div class="col-md-6 offset-md-1">
        <h3 class="box_header">Cursos adicionais</h3>
      </div>
      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label for="curriculum-children">Experiência em Espanhol</label>
            <select
              id="espanhol"
              class="form-control form-select"
              name="espanhol"
            >
              <option value="">Selecione</option>
              <option value="0">Nenhuma</option>
              <option value="1">Básico</option>
              <option value="2">Intermediário</option>
              <option value="3">Avançado</option>
            </select>
          </div>

          <div class="col-md-6 mt-5">
            <label for="curriculum-children">Experiência em Inglês</label>
            <select id="ingles" class="form-control form-select" name="ingles">
              <option value="">Selecione</option>
              <option value="0">Nenhuma</option>
              <option value="1">Básico</option>
              <option value="2">Intermediário</option>
              <option value="3">Avançado</option>
            </select>
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label for="curriculum-children">Experiência em Excel</label>
            <select id="excel" class="form-control form-select" name="excel">
              <option value="">Selecione</option>
              <option value="0">Nenhuma</option>
              <option value="1">Básico</option>
              <option value="2">Intermediário</option>
              <option value="3">Avançado</option>
            </select>
          </div>

          <div class="col-md-6 mt-5">
            <label for="curriculum-children">Experiência em Informática</label>
            <select
              id="informatica"
              class="form-control form-select"
              name="informatica"
            >
              <option value="">Selecione</option>
              <option value="0">Nenhuma</option>
              <option value="1">Básico</option>
              <option value="2">Intermediário</option>
              <option value="3">Avançado</option>
            </select>
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label for="curriculum-children">Experiência em Internet</label>
            <select id="net" class="form-control form-select" name="net">
              <option value="">Selecione</option>
              <option value="0">Nenhuma</option>
              <option value="1">Básico</option>
              <option value="2">Intermediário</option>
              <option value="3">Avançado</option>
            </select>
          </div>

          <div class="col-md-6 mt-5">
            <label for="curriculum-children">Experiência em PowerPoint</label>
            <select id="pw" class="form-control form-select" name="pw">
              <option value="">Selecione</option>
              <option value="0">Nenhuma</option>
              <option value="1">Básico</option>
              <option value="2">Intermediário</option>
              <option value="3">Avançado</option>
            </select>
          </div>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label for="curriculum-children">Experiência em Word</label>
            <select id="wd" class="form-control form-select" name="wd">
              <option value="">Selecione</option>
              <option value="0">Nenhuma</option>
              <option value="1">Básico</option>
              <option value="2">Intermediário</option>
              <option value="3">Avançado</option>
            </select>
          </div>
        </div>
      </div>

      <div class="col-md-10 offset-md-1">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label for="telefone">Outros</label>
            <input
              type="text"
              class="form-control"
              name="CurriculumCourseAdditional[outros][courses]"
              value=""
            />
          </div>
        </div>
      </div>

      <br />

      <div class="col-md-6 offset-md-1">
        <h3 class="box_header">Experiência Profissional</h3>
      </div>

      <div id="clone04">
        <div class="col-md-6 offset-md-1">
          <h4
            class="box_header font-weight-bolder text-smalt-blue text-uppercase"
          >
            EXPERIÊNCIA <span id="count">01</span>
          </h4>
        </div>

        <div class="col-md-6 offset-md-1">
          <div class="row">
            <div class="col-md-6 mt-5">
              <label>Empresa</label>
              <input type="text" class="form-control" name="empresa" value="" />
            </div>

            <div class="col-md-6 mt-5">
              <label>Cargo</label>
              <input v-model="message" class="form-control" />
            </div>
          </div>
        </div>

        <div class="col-md-6 offset-md-1">
          <div class="row">
            <div class="col-md-6 mt-5">
              <label class="mb-1">Período de</label>
              <input type="text" id="de" class="form-control" name="de" />
            </div>
            <div class="col-md-6 mt-5">
              <label>Até</label>
              <br />
              <input type="text" id="ate" class="form-control" name="ate" />
            </div>
          </div>
        </div>
      </div>

      <div id="clone05"></div>

      <div class="col-md-6 offset-md-1">
        <div class="text-right col-md-12 mt-4">
          <button class="bg btn btn-primary" type="button" @click="clone04()">
            Experiência Profissional +
          </button>
        </div>
      </div>

      <div class="col-md-6 offset-md-1">
        <h3 class="box_header">Informações Adicionais</h3>
      </div>

      <div class="col-md-6 offset-md-1">
        <div class="form-group field-curriculum-text validating">
          <label for="curriculum-text">Informações adicionais</label>
          <textarea
            id="curriculum-text"
            class="form-control is-valid form-control"
            name="Curriculum[text]"
            rows="5"
            aria-invalid="false"
          ></textarea>
          <div class="invalid-feedback"></div>
        </div>
      </div>

      <br />

      <div class="col-md-6 offset-md-1">
        <label for="curriculum-text">Informações adicionais</label>
        <select
          id="curriculum-availability"
          class="form-control is-invalid form-select"
          name="Curriculum[availability]"
          aria-required="true"
          aria-invalid="true"
        >
          <option value="">Selecione</option>
          <option value="M">Manhã</option>
          <option value="T">Tarde</option>
          <option value="N">Noite</option>
          <option value="I">Integral</option>
        </select>
      </div>

      <br />

      <div class="col-md-6 offset-md-1">
        <label for="curriculum-text">Área pretendida</label>
        <select
          id="curriculum-area_intended_id"
          class="form-control is-invalid form-select"
          name="Curriculum[area_intended_id]"
          aria-required="true"
          aria-invalid="true"
        >
          <option value="">Selecione</option>
          <option value="20">Administrativo</option>
          <option value="19">Aprendizes</option>
          <option value="23">Central de Guias</option>
          <option value="2">Compras</option>
          <option value="10">Comunicação</option>
          <option value="22">Contabilidade</option>
          <option value="3">Copa</option>
          <option value="4">Enfermagem</option>
          <option value="5">Farmácia</option>
          <option value="6">Faturamento</option>
          <option value="7">Financeiro</option>
          <option value="8">Fisioterapia</option>
          <option value="9">Informática</option>
          <option value="11">Limpeza</option>
          <option value="18">Medicina do Trabalho</option>
          <option value="21">Motorista</option>
          <option value="12">Nutrição</option>
          <option value="14">Portaria</option>
          <option value="13">Psicologia</option>
          <option value="15">Recepção</option>
          <option value="16">Recursos Humanos</option>
          <option value="1">Serviço Social</option>
          <option value="17">Tesouraria</option>
        </select>
      </div>

      <br />

      <div class="col-md-6 offset-md-1">
        <div
          class="form-group field-curriculum-area_intended_function_id required validating"
        >
          <label for="curriculum-area_intended_function_id">Função</label>
          <select
            id="curriculum-area_intended_function_id"
            class="form-control is-invalid form-select"
            name="Curriculum[area_intended_function_id]"
            aria-required="true"
            aria-invalid="true"
          ></select>
        </div>
      </div>

      <br />

      <div class="col-md-8 offset-md-1">
        <button type="submit" class="more blue bg btn btn-primary">
          Enviar
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";
import { required } from "@vuelidate/validators";

export default {
  el: "#app",
  data() {
    return {
      cep: "",
      address: {},
      nome: "",
      email: "",
      senha: "",
      dtns: "",
      cpf: "",
      nameBlured: false,
      emailBlured: false,
      senhaBlured: false,
      dtnsBlured: false,
      cpfBlured: false,
    };
  },
  validations() {
    return {
      nome: {
        required,
      },
    };
  },
  methods: {
    searchCep() {
      axios
        .get(`https://viacep.com.br/ws/${this.cep}/json/`)
        .then((response) => {
          this.address = response.data;
          document.getElementById("logradouro").value = this.address.logradouro;
          document.getElementById("bairro").value = this.address.bairro;
          document.getElementById("localidade").value = this.address.localidade;
          document.getElementById("uf").value = this.address.uf;

          var opt = document.createElement("option");
          opt.value = this.address.localidade;
          opt.innerHTML = this.address.localidade;
          document.getElementById("localidade").appendChild(opt);

          var opt2 = document.createElement("option");
          opt2.innerHTML = this.address.uf;
          opt2.value = this.address.uf;
          document.getElementById("uf").appendChild(opt2);
          // option of select with value of uf
          console.log(this.address);
        })
        // depois que limpar o campo, limpar o objeto
        .catch((error) => {
          this.address = {};
          document.getElementById("logradouro").value = "";
          document.getElementById("bairro").value = "";
          document.getElementById("localidade").value = "";
          document.getElementById("uf").value = "";
          console.log(error);
        });
    },
    validate: function () {
      this.nameBlured = true;
      if (this.validanome(this.nome)) {
        this.valid = true;
      }
    },
    validaNome: function (nome) {
      if (nome.length < 3) {
        return false;
      }
      return true;
    },
    validaEmail: function (email) {
      if (email.length < 3) {
        return false;
      }
      return true;
    },
    validaSenha: function (senha) {
      if (senha.length < 3) {
        return false;
      }
      return true;
    },
    validaDtns: function (dtns) {
      if (dtns.length < 3) {
        return false;
      }
      return true;
    },
    validaCpf: function (cpf) {
      if (cpf.length < 3) {
        return false;
      }
      return true;
    },
    // clone
    Clone() {
      const node = document.getElementById("clone");
      const clone = node.cloneNode(true);
      document.getElementById("clone2").appendChild(clone);
    },
    clone04() {
      const node = document.getElementById("clone04");
      const clone04 = node.cloneNode(true);
      document.getElementById("clone05").appendChild(clone04);
    },
  },
};
</script>

<style>
#main {
  overflow: auto;
}

h3.box_header {
  margin: 0 0 20px;
  font-size: 24px;
  margin: 20px 0 10px;
  font-weight: 400;
  border-bottom: 2px solid #ddd;
  padding-bottom: 15px;
  line-height: 30px;
}
.dados_pessoais {
  text-align: left;
  color: blue;
  font-size: large;
}
.nome {
  text-align: left;
  color: blue;
}
.email {
  color: blue;
}
.senha {
  color: blue;
}
.dtns {
  color: blue;
}
.cpf {
  color: blue;
}
.pfd {
  color: blue;
}
.qfd {
  color: blue;
}
.ec {
  color: blue;
}
.sx {
  color: blue;
}
.pd {
  color: blue;
}
.qd {
  color: blue;
}
.cep {
  color: blue;
}
.endereco {
  color: blue;
}
.numero {
  color: blue;
}
.bairro {
  color: blue;
}
.complemento {
  color: blue;
}
.cidades {
  color: blue;
}
.estados {
  color: blue;
}
.tr {
  color: blue;
}
.tc {
  color: blue;
}
.ramal {
  color: blue;
}
.telefone_celular {
  color: blue;
}
.ad {
  color: blue;
}
.qd {
  color: blue;
}
</style>
