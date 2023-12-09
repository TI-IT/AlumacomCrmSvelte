<script>
    let email = "";
    let password = "";
    let confirmPass = "";
    let error = false;
    let register = false;

    // Обработка авторизации
    function handleAuthenticate() {
        if (!email || !password || (register && !confirmPass)) {
            error = true;
            return;
        }
    }
</script>

<!--Форма логина-->
<div class="authContainer">
    <div>
        <a href="https://youtu.be/TIbL0VOE900?t=1426">Lesson</a>
    </div>
    <form>
        <h1>{register ? "Регистрация" : "Войти"}</h1>
        {#if error}
            <p class="error">Введенная информация не верна</p>
        {/if}
        <label>
            <p class={email ? 'above' : 'center'}>Email</p>
            <input bind:value={email} type="email" placeholder="Email"/>
        </label>
        <label>
            <p class={password ? 'above' : 'center'}>Password</p>

            <input bind:value={password} type="password" placeholder="password"/>
        </label>
        <label>
            <p class={confirmPass ? 'above' : 'center'}>Confirm password</p>

            <input bind:value={confirmPass} type="password" placeholder="Confirm password"/>
        </label>
        <button type="button">Зарегистрировать</button>
    </form>
    <div class="options">
        <p>или</p>
        {#if register}
            <div>
                <p>Аккаунт существует?</p>
                <p>Войти</p>
            </div>
            {:else}
            <div>
                <p>Отсутствует учетная запись?</p>
                <p>Зарегистрируйтесь</p>
            </div>
            {/if}
    </div>
</div>

<style>
    .authContainer {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        flex: 1;
        padding: 24px;
    }

    form {
        display: flex;
        flex-direction: column;
        gap: 14px;
    }

    form,
    .options {
        width: 400px;
        max-width: 100%;
        margin: 0 auto;
    }

    h1 {
        text-align: center;
        font-size: 3rem;
    }

    form input {
        width: 100%;
        border: none;
        background: transparent;
        color: white;
        padding: 14px;
    }

    form label {
        position: relative;
        border: 1px solid navy;
        border-radius: 5px;
    }

    form input:focus {
        border: none;
        outline: none;
    }

    form label:focus-within {
        border-color: blue;
    }

    form button {
        background: navy;
        color: white;
        border: none;
        padding: 14px 0;
        border-radius: 5px;
        cursor: pointer;
        font-size: 1rem;
    }

    form button:hover {
        background: blue;
    }

    .above,
    .center {
        position: absolute;
        transform: translateY(-50%);
        pointer-events: none;
        color: white;
        border-radius: 4px;
        padding: 0 6px;
        font-size: 0.8rem;
    }

    .above {
        top: 0;
        left: 24px;
        background: navy;
        border: 1px solid blue;
        font-size: 0.7rem;
    }

    .center {
        top: 0;
        left: 6px;
        border: 1px solid transparent;
        opacity: 0;
    }

    .error {
        color: coral;
        font-size: 0.9rem;
    }

    .options {
        padding: 14px 0;
        overflow: hidden;
        font-size: 0.9rem;
    }

    .options > p {
        position: relative;
        text-align: center;
        width: fit-content;
        margin: 0 auto;
        padding: 0 8px;
    }

    .options > p::after,
    .options > p::before {
        position: absolute;
        content: '';
        top: 50%;
        transform: translateY(-50%);
        width: 100vw;
        height: 1.5px;
        background: white;
    }

    .options > p::after {
        right: 100%;
    }
    .options > p::before {
        left: 100%;
    }

</style>